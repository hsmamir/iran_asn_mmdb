# Iran ASN MMDB

This repository contains a MaxMind DB (MMDB) file that provides information about Autonomous System Numbers (ASNs) for ISPs in Iran. This database is useful for applications that require accurate ISP identification, IP geolocation, and network data analysis.

## Features

- **Up-to-Date ASN Data**: Contains the latest ASN allocations and ISP information for networks operating in Iran.
- **Efficient Lookups**: Optimized for quick data retrieval, suitable for integration into geo-location services and other applications.
- **Comprehensive Coverage**: Includes a wide range of ISPs across different regions in Iran.

## Formats

In addition to the MMDB file, this repository also provides the ASN data in CSV and JSON formats for easier integration into various applications.

### CSV Format

The CSV file contains the ASN data with the following columns:

- `network_address`: The network address in CIDR notation.
- `name`: The name of the Internet Service Provider (ISP).

Here’s a sample of the CSV format:

```csv
network_address,name
2.57.3.0/24,Enteghal Dadeh Mahan Co. PJSC
2.188.232.0/23,Respina Networks & Beyond PJSC
2.188.235.0/24,Respina Networks & Beyond PJSC
```

### JSON Format

The JSON file provides a structured representation of the ASN data. Here’s a sample of the JSON format:

```json
[
    {
        "network_address": "2.57.3.0/24",
        "name": "Enteghal Dadeh Mahan Co. PJSC"
    },
    {
        "network_address": "2.188.232.0/23",
        "name": "Respina Networks & Beyond PJSC"
    },
    {
        "network_address": "2.188.235.0/24",
        "name": "Respina Networks & Beyond PJSC"
    }
]
```

## MMDB Creation

The MMDB file in this repository has been created from the provided CSV data, ensuring that the ASN information is accurately represented and up-to-date.

## Usage

### Installation

You can download the MMDB, CSV, or JSON files directly from this repository or integrate it into your project as follows:

```bash
git clone https://github.com/hsmamir/iran_asn_mmdb.git
cd iran_asn_mmdb
```

### Accessing the Files

Once cloned, you can find the MMDB, CSV, and JSON files in the repository directory. Use them in your applications as needed.

#### Example (Python for CSV and JSON)

Here’s a simple example of how to read the CSV and JSON files in Python:

```python
import csv
import json

# Reading the CSV file
with open('path/to/your/data.csv', mode='r', encoding='utf-8') as csvfile:
    reader = csv.DictReader(csvfile)
    for row in reader:
        print(f"Network Address: {row['network_address']}, ISP: {row['name']}")

# Reading the JSON file
with open('path/to/your/data.json', mode='r', encoding='utf-8') as jsonfile:
    data = json.load(jsonfile)
    for entry in data:
        print(f"Network Address: {entry['network_address']}, ISP: {entry['name']}")
```

### Accessing the MMDB File

Once cloned, you can find the MMDB file in the repository directory. Use it in your applications with libraries that support MMDB files, such as:

- **MaxMind's GeoIP2** for Python
- **mmdblookup** for command-line usage

### Example (Python for MMDB)

Here’s a simple example of how to use the MMDB file in a Python application:

```python
import geoip2.database

# Path to the MMDB file
mmdb_file_path = 'path/to/your/mmdb_file.mmdb'

# Create a reader object
reader = geoip2.database.Reader(mmdb_file_path)

# Example IP address lookup
try:
    response = reader.asn('8.8.8.8')
    print(f'ASN: {response.autonomous_system_number}, ISP: {response.autonomous_system_organization}')
except Exception as e:
    print(f'Error: {e}')
finally:
    reader.close()
```

## Updates

This repository will be periodically updated to reflect changes in ASN allocations and ISP information. You can check the release notes for details on updates and changes made.

## Contributing

Contributions are welcome! If you have suggestions or improvements, please open an issue or submit a pull request.

## License

This project is licensed under a **Free License**, allowing free use and distribution for all individuals. You are free to use, modify, and share this database without restriction.

## Acknowledgments

- Thank you to MaxMind for providing the tools and infrastructure for working with MMDB files.
- Special thanks to the contributors who help keep this database up-to-date.
