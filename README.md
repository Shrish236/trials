# GDBYantra - An automation tool for ASIC testing

GDBYantra is an automation tool to run tests on ASIC through python. The main script compiles all tests, executes them, collects the results, and sends an email with the results in an Excel file. The script also sends the results to Splunk for further analysis through visual dashboards.

## Prerequisites

Before running the script, ensure you have all the requirements installed.

You can install the required libraries using `pip`:

```bash
pip install -r requirements.txt
```

## Configuration

### secureiot_automation_config.json

Edit the configuration file according to your specifications.

## Running the Script

To run the script, simply execute:

```bash
python chipautomationchild.py
```

The script will perform the following steps:

1. **Compile All Tests**: Calls the `makeall` module to compile all tests.
2. **Read Configuration**: Reads the configuration from `secureiot_automation_config.json`.
3. **Read Test Data**: Reads test names and IDs from a remote google sheets file.
4. **Execute Tests**: Runs each test using GDB through pygdbmi and collects the results.
5. **Generate Results**: Generates an Excel file with the test results.
6. **Send Email**: Sends an email with the test results.
7. **Send Data to Splunk**: Sends the test results to Splunk if enabled.

## Splunk Integration

If Splunk integration is enabled, the script will send the test results to the specified Splunk HEC endpoint. Ensure the HEC token and URL are correctly configured.

## Steps before execution

- Ensure requirements are installed.
- Edit the configuration file accordingly.
- Fork the SecureIoT-PSV Repository and add necessary modules and tests as needed.
- Ensure the [Automation Modules](https://docs.google.com/spreadsheets/d/1ZKWa0orwQP4YH0jsKAjOjsciPtcXv5O2wGxGBeK7qXg/edit?gid=1261736987#gid=1261736987) sheet is up and configured correctly. If sheet is going to be changed, make sure to publish the google sheet as excel and change the link in line 163 and 185.
- Ensure openocd-ftdi terminal is up and does not have any existing connections. 
