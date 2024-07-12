# Answer

## Rust

I think this one works right...

```rust
const PROGRAM: &str = r#"
    ++++++++++[>+++++++>++++++++++>+++>+<<<<-]>++.>+.+++++++..+++.>++.<<+++++++++++++++.>.+++.------.--------.>+.>.
"#;
const INCREMENT_DATAPOINTER: char = '>';
const DECREMENT_DATAPOINTER: char = '<';
const INCREMENT_BYTE: char = '+';
const DECREMENT_BYTE: char = '-';
const OUTPUT_BYTE: char = '.';
const INPUT_BYTE: char = ',';
const JUMP_FORWARD: char = '[';
const JUMP_BACKWARD: char = ']';

enum Instruction {
    IncrementDataPointer,
    DecrementDataPointer,
    IncrementByte,
    DecrementByte,
    OutputByte,
    InputByte,
    JumpBlock(Vec<Instruction>),
}

fn parse<T: AsRef<str>>(input: T) -> Result<Vec<Instruction>, &'static str> {
    let mut instructions = Vec::new();
    let mut chars = input.as_ref().chars().peekable();
    while let Some(&c) = chars.peek() {
        match c {
            INCREMENT_DATAPOINTER => instructions.push(Instruction::IncrementDataPointer),
            DECREMENT_DATAPOINTER => instructions.push(Instruction::DecrementDataPointer),
            INCREMENT_BYTE => instructions.push(Instruction::IncrementByte),
            DECREMENT_BYTE => instructions.push(Instruction::DecrementByte),
            OUTPUT_BYTE => instructions.push(Instruction::OutputByte),
            INPUT_BYTE => instructions.push(Instruction::InputByte),
            JUMP_FORWARD => {
                chars.next();
                let mut block = Vec::new();
                while let Some(&c) = chars.peek() {
                    block.push(c);

                    if c == JUMP_BACKWARD {
                        break;
                    }
                    chars.next();
                }
    
                if block.last() != Some(&JUMP_BACKWARD) {
                    return Err("Expected ']' to close block");
                }

                let parsed_block = parse(block.iter().collect::<String>().as_str())?;
                instructions.push(Instruction::JumpBlock(parsed_block));
            }
            _ => (),
        }
        chars.next();
    }
    Ok(instructions)
}

fn process_instruction(instruction: &Instruction, data: &mut Vec<u8>, data_pointer: &mut usize) {
    match instruction {
        Instruction::IncrementDataPointer => increment_data_pointer(data_pointer),
        Instruction::DecrementDataPointer => decrement_data_pointer(data_pointer),
        Instruction::IncrementByte => increment_byte(data, *data_pointer),
        Instruction::DecrementByte => decrement_byte(data, *data_pointer),
        Instruction::OutputByte => output_byte(data, *data_pointer),
        Instruction::InputByte => input_byte(data, *data_pointer),
        Instruction::JumpBlock(ref block) => process_jump_block(block, data, data_pointer),
    }
}

fn increment_data_pointer(data_pointer: &mut usize) {
    *data_pointer += 1;
}

fn decrement_data_pointer(data_pointer: &mut usize) {
    if *data_pointer > 0 {
        *data_pointer -= 1;
    }
}

fn increment_byte(data: &mut Vec<u8>, data_pointer: usize) {
    data[data_pointer] += 1;
}

fn decrement_byte(data: &mut Vec<u8>, data_pointer: usize) {
    data[data_pointer] = data[data_pointer].saturating_sub(1);
}

fn output_byte(data: &mut Vec<u8>, data_pointer: usize) {
    print!("{}", data[data_pointer] as char);
}

fn input_byte(data: &mut Vec<u8>, data_pointer: usize) {
    let mut input = String::new();
    std::io::stdin().read_line(&mut input).unwrap();
    data[data_pointer] = input.chars().next().unwrap() as u8;
}

fn process_jump_block(block: &[Instruction], data: &mut Vec<u8>, data_pointer: &mut usize) {
    while data[*data_pointer] != 0 {
        for instruction in block {
            process_instruction(instruction, data, data_pointer);
        }
    }
}

fn evaluate(instructions: &[Instruction]) {
    let mut data: Vec<u8> = vec![0; 30000];
    let mut data_pointer = 0;
    let mut instruction_pointer = 0;

    while instruction_pointer < instructions.len() {
        process_instruction(&instructions[instruction_pointer], &mut data, &mut data_pointer);
        instruction_pointer += 1;
    }
}
#fn main() {
    #let instructions = parse(PROGRAM).unwrap();
    #evaluate(&instructions);
#}
```