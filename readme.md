# SafeDB - Database Backup Utility [WIP]

This Python-based utility allows you to backup MariaDB and PostgreSQL databases with integrity checks and retention policies. It supports local backups as well as cloud storage options like Azure Blob Storage.

## Features

- Support for MariaDB and PostgreSQL databases
- Local and cloud storage backup options (Azure Blob Storage)
- Integrity checks using SHA-256 hash
- Configurable retention policy
- Logging of all operations

## Installation

1. Clone this repository:
   ```
   git clone https://github.com/marchelzi/SafeDB.git
   cd SafeDB
   ```

2. Install the required Python packages:
   ```
   pip install -r requirements.txt
   ```

3. Ensure you have the necessary database client tools installed:
   - For MariaDB: `mariadb-dump`
   - For PostgreSQL: `pg_dump`

## Configuration

1. Copy the `config.ini.example` inside src file to `config.ini`:
   ```
   cp config.ini.example config.ini
   ```

2. Edit `config.ini` to set up your database connections, backup destinations, and other options.

## Usage

Run the script with:

```
python src/main.py backup --config /path/to/your/config.ini
```

## Verifying Backups [Work in Progress]

The utility computes a SHA-256 hash of each backup file and logs it. To verify a backup:

1. Find the hash in the log file.
2. Compute the hash of your backup file:
   ```
   sha256sum your_backup_file.sql.gz
   ```
3. Compare the two hashes. They should match if the file is intact.

## TODO!

- [ ] Implement the `verify` command to verify the integrity of backup files.
- [ ] Implement the `restore` command to restore databases from backup files.
- [ ] Add support for more cloud storage options (e.g., AWS S3, Google Cloud Storage).
- [ ] Add support for more databases (e.g., MySQL, SQLite).
- [ ] Add more configuration options for advanced use cases.
- [ ] Add unit tests and CI/CD pipeline.
- [ ] Improve documentation and error handling.
- [ ] Add support for Windows systems.

## Done ✓
- [x] Implement the `backup` command to create database backups.
- [x] Add support for MariaDB and PostgreSQL databases.
- [x] Add support for local backup destinations.
- [x] Add support for Azure Blob Storage as a backup destination.
- [x] Implement retention policy to delete old backups.
- [x] Add logging of all operations.
- [x] Add configuration file for easy setup.
- [x] Add command-line arguments for flexibility.

## Security Notes

- Ensure that `config.ini` has restricted permissions (e.g., `chmod 600 config.ini` on Unix-like systems).
- Consider using environment variables for sensitive information instead of storing them in the config file.

## Troubleshooting

- Check the log file for detailed error messages and operation logs.
- Ensure you have the necessary permissions to access the databases and backup destinations.
- Verify that all required tools (`mariadb-dump`, `pg_dump`) are installed and accessible in your system's PATH.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the LICENSE file for details.
