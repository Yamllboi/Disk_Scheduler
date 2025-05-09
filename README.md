# Disk Scheduling Algorithms Simulator

This program simulates and compares three common disk scheduling algorithms: FCFS, SCAN, and C-SCAN. It allows users to evaluate how these different algorithms perform when handling disk access requests.

## Features

- Simulates a disk with 5,000 cylinders (numbered 0-4,999)
- Generates 1,000 random cylinder requests or accepts custom user input
- Takes the initial disk head position as input
- Processes requests using three different algorithms:
  - FCFS (First-Come-First-Served)
  - SCAN (Elevator algorithm)
  - C-SCAN (Circular SCAN)
- Displays detailed movement of the disk head for each algorithm
- Reports the total head movement required by each algorithm
- Identifies the most efficient algorithm for the given requests

## Requirements

- Python 3.x

## How to Use

1. Run the script:
   ```
   python disk_scheduling.py
   ```

2. Follow the interactive prompts:
   - Select an option (run with random requests, enter custom requests, or exit)
   - Enter the initial head position (0-4999)
   - If entering custom requests, provide comma-separated cylinder numbers

3. The program will display the results, showing:
   - Detailed head movements for each algorithm
   - Total head movement for each algorithm
   - The most efficient algorithm for the given scenario

## Algorithm Descriptions

### FCFS (First-Come-First-Served)

The simplest scheduling algorithm that processes requests in the order they arrive without any optimization.

- **Example**: If the head is at position 50 and requests are [95, 180, 34, 119]:
  1. Move from 50 to 95 (45 cylinders)
  2. Move from 95 to 180 (85 cylinders)
  3. Move from 180 to 34 (146 cylinders)
  4. Move from 34 to 119 (85 cylinders)
  5. Total movement: 361 cylinders

### SCAN (Elevator Algorithm)

Similar to an elevator, the disk head moves in one direction, servicing all requests in its path until it reaches the end of the disk, then reverses direction.

- **Example**: If the head is at position 50, requests are [95, 180, 34, 119], and we start moving up:
  1. Move from 50 to 95 (45 cylinders)
  2. Move from 95 to 119 (24 cylinders)
  3. Move from 119 to 180 (61 cylinders)
  4. Move from 180 to 4999 (end of disk) (4819 cylinders)
  5. Move from 4999 to 34 (4965 cylinders)
  6. Total movement: 9914 cylinders

### C-SCAN (Circular SCAN)

An enhancement of SCAN where the head moves in only one direction. When it reaches the end, it immediately returns to the beginning and continues scanning.

- **Example**: If the head is at position 50, requests are [95, 180, 34, 119], and we move toward higher cylinders:
  1. Move from 50 to 95 (45 cylinders)
  2. Move from 95 to 119 (24 cylinders)
  3. Move from 119 to 180 (61 cylinders)
  4. Move from 180 to 4999 (end of disk) (4819 cylinders)
  5. Jump from 4999 to 0 (4999 cylinders)
  6. Move from 0 to 34 (34 cylinders)
  7. Total movement: 9982 cylinders

## Performance Considerations

- **FCFS**: Simple but often inefficient, especially with scattered requests
- **SCAN**: Generally efficient, reduces total head movement, and prevents request starvation
- **C-SCAN**: Provides more uniform waiting times but may require more total head movement than SCAN

For large disks or systems with many random access patterns, SCAN and C-SCAN typically outperform FCFS significantly.

## Further Reading

For more information on disk scheduling algorithms, refer to:
- Operating Systems textbooks
- Computer Architecture references
- Mass Storage Structure chapters in Systems Programming guides
