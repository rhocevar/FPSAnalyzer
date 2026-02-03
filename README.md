## FPS (Frames Per Second) Analyzer

A command-line tool that processes FPS performance log files for a given real-time game simulation and reports statistical summaries (min/max or average FPS) for a given game Act.

### Prerequisites

- Python 3.9.6+

No external dependencies are required — the tool uses only the Python standard library (`sys`, `os`, `json`).

### Usage

```
python d3fps.py <ACT> <CALC_TYPE> <DATA_DIR>
```

| Argument    | Description                                          |
|-------------|------------------------------------------------------|
| `ACT`       | Game act to analyze: `A1`, `A2`, `A3`, or `A4`      |
| `CALC_TYPE` | Calculation type: `minmax` or `avg`                  |
| `DATA_DIR`  | Path to a directory containing JSON performance logs |

**Examples:**

```
python d3fps.py A1 minmax ./FPSLogs   # Min FPS: 37.84, Max FPS: 61.96
python d3fps.py A2 avg ./FPSLogs      # Average FPS: 58.235...
```

### Data Format

Each JSON log file contains a `collections` array. Each collection includes metadata (`act`, `world`, `scene`, etc.) and a `samples` array of performance measurements. Each sample records `fps`, timestamp, rendering batch/triangle counts, particle metrics, and CPU/GPU bound indicators.

### Jenkins Integration

The project includes a `Jenkinsfile` that defines a parameterized pipeline with dropdown selections for `ACT` and `CALC_TYPE`, and a configurable `LOGS_DIR` (defaults to `./FPSLogs`). The pipeline is configured as **Pipeline script from SCM**.

### Tools Used

- Python 3.9.6
- PyCharm IDE
- Jenkins 2.504.3

### References

- [Jenkins Pipeline Tutorials](https://www.jenkins.io/doc/tutorials/#pipeline)
