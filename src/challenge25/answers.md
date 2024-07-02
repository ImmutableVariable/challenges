# Answer

## JavaScript

```javascript
const seriesTypes = {
    arithmetic: 'arithmetic',
    geometric: 'geometric'
}

/**
 * Get the type of series, either arithmetic or geometric
 * @param {number[]} sequence The sequence to find the type of
 * @returns {string|null} the type of series
 */
function getSeriesType(sequence) {
    if (sequence.length < 3) throw new Error("Sequence is not long enough, 3 items required. Found: " + sequence.length);

    const differences = new Set();
    const ratios = new Set();

    for (let i = 1; i < sequence.length; i++) {
        const difference = sequence[i] - sequence[i - 1]; // a arthimetic series will only have one difference between all numbers exp: 2, 4, 6, 8 (diff: 2)
        const ratio = sequence[i] / sequence[i - 1]; // For this, the ratio is the same, exp: 4, 16, 64 (ratio: 4)

        // store each value found then in set, a set can only have one unique value, so if there is anymore its not that series type
        differences.add(difference);
        ratios.add(ratio);
    }

    if (differences.size === 1) return seriesTypes.arithmetic;
    if (ratios.size === 1) return seriesTypes.geometric;

    return null;
}

/**
 * Find the nth term in a geometric or arithmetic sequence
 * @param {number[]} sequence The sequence to find the nth term in
 * @param {number} n The nth term to find
 * @returns {number|null} the nth term of the series
 */
function findNthTermInSequence(sequence, n) {
    const type = getSeriesType(sequence);
    if (type === seriesTypes.arithmetic) {
        const difference = sequence[1] - sequence[0];
        return sequence[sequence.length - 1] + difference * (n - sequence.length);
    } else if (type === seriesTypes.geometric) {
        const ratio = sequence[1] / sequence[0];
        return sequence[sequence.length - 1] * Math.pow(ratio, n - sequence.length);
    } else {
        throw new Error("Unsupported series type")
    }
}
```