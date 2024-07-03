# Answer

## Rust - Sakamoto's method
```rust
const DAYS: [&str; 7] = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];

fn get_day_of_week(day: i32, month: i32, year: i32) -> String {
    let t = [0, 3, 2, 5, 0, 3, 5, 1, 4, 6, 2, 4];
    let y = year - if month < 3 { 1 } else { 0 };
    let w = (y + y / 4 - y / 100 + y / 400 + t[(month - 1) as usize] + day) % 7;
    DAYS[w as usize].to_string()
}

#fn main() {
println!("{}", get_day_of_week(1, 1, 2020));
#}
```

## Rust - [Schwerdtfeger's method](https://en.wikipedia.org/wiki/Determination_of_the_day_of_the_week#Schwerdtfeger's_method)
```rust
const DAYS: [&str; 7] = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];

fn get_day_of_week(day: i32, month: i32, year: i32) -> String {
    let c = if month > 2 { year / 100 } else { (year - 1) / 100 };
    let g = if month > 2 { year - 100 * c } else { year - 1 - 100 * c };
    let e = [0, 3, 2, 5, 0, 3, 5, 1, 4, 6, 2, 4];
    let f = [0, 5, 3, 1];

    let w = (day + e[(month - 1) as usize] + f[(c % 4) as usize] + g + (g / 4)) % 7;
    DAYS[w as usize].to_string()
}

#fn main() {
println!("{}", get_day_of_week(1, 1, 2020));        
#}
```

### Equivalent JavaScript
```javascript
const days = ['Sunday', 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday'];

function getDayOfTheWeek(day, month, year) { 
    let c = Math.floor(month > 2 ? year / 100 : (year - 1) / 100);
    let g = month > 2 ? year - 100 * c : year - 1 - 100 * c;
    const e = [0, 3, 2, 5, 0, 3, 5, 1, 4, 6, 2, 4];
    const f = [0, 5, 3, 1]

    let w = (day + e[month - 1] + f[c % 4] + g + Math.floor((g/4))) % 7;
    return days[w];
}
```

## Python - Simplified Zeller w/ Keith's Month-Length Equation

```py
import math

days = ["Sat", "Sun", "Mon", "Tue", "Wed", "Thu", "Fri"]

def h(d, m, y):
    if m == 1 or m == 2:
        y -= 1
        m += 12
    return days[((d+math.floor((((23*m)/9)+4))+y+math.floor(y/4)-math.floor(y/100)+math.floor(y/400)) % 7) - 1]
```

### Rust Equivalent

```rust
const DAYS: [&str; 7] = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];

fn get_day_of_week(day: i32, mut month: i32, mut year: i32) -> String {
    if month < 3 {
        month += 12;
        year -= 1;
    }
    let d = day;
    let k = year % 100;
    let j = year / 100;
    let day_of_week = (d + ((13 * (month + 1)) / 5) + k + (k / 4) + (j / 4) + 5 * j) % 7;

    DAYS[(day_of_week + 6) as usize % 7].to_string()
}

#fn main() {
println!("{}", get_day_of_week(1, 1, 2020));
#}
```