# Handbook Standards

Every topic should contain:

- Overview
- Why it exists
- Internal working
- Advantages
- Disadvantages
- Trade-offs
- Complexity
- Interview Questions
- Common Mistakes
- Real-world Usage
- Related Topics
- Resources
- Revision History

Every explanation should answer:

- What?
- Why?
- How?
- When?
- Why not another solution?

## API Guarantees vs Assumptions

Always distinguish between:

- What Java **guarantees**
- What **usually** happens
- What developers **assume**

Examples: HashMap O(1) average (not guaranteed worst case), PriorityQueue priority ordering (not FIFO), Stream API vs Collections utility methods.
