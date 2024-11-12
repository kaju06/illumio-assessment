# Flow Log Mapper

The program parses a file containing flow log data and maps each row to a tag based on a lookup table, as per the given requirements.

## Assumptions

- The program only supports logs in the default format and version 2.
- Case-insensitive matching is implemented for protocols (e.g., "tcp" or "TCP").
- Any row that does not have a matching tag in the lookup table is counted as "Untagged"

## Files and Input Format

1. **Lookup Table (lookup_table.csv):**
   - A CSV file containing columns `dstport`, `protocol`, and `tag`.
   - Sample format:
     ```
     dstport,protocol,tag
     25,tcp,sv_P1
     68,udp,sv_P2
     ```

2. **Flow Log File (flow_log_data.txt):**
   - Each line represents a log in the default format:
     ```
     version account-id eni-id srcaddr dstaddr srcport dstport protocol packets bytes start end action log-status
     ```

## Output Format (output.txt)

The program generates an output file (output.txt) with the following sections:

1. **Tag Counts:**
   - Displays the count of each tag found in the logs, along with the count of "Untagged" entries.

2. **Port/Protocol Combination Counts:**
   - Shows the count of each port/protocol combination.

## How to Run the Program

1. Place `lookup_table.csv` and `flow_log_data.txt` in the same directory as `flow_log_mapper.py`.
2. Run the script:
   ```bash
   python3 flow_log_mapper.py
