import sqlite3
import datetime


class TelemetryDB:
    def __init__(self):
        # This creates a database file called 'thermal_grid.db' in your project
        self.conn = sqlite3.connect("thermal_grid.db", check_same_thread=False)
        self.cursor = self.conn.cursor()

        # This builds the table (the spreadsheet) to hold our data
        self.cursor.execute('''
                            CREATE TABLE IF NOT EXISTS metrics
                            (
                                timestamp
                                TEXT,
                                cpu_load
                                REAL,
                                cpu_temp
                                REAL,
                                ram_usage
                                REAL,
                                vram_clock
                                REAL
                            )
                            ''')
        self.conn.commit()

    def log_metrics(self, cpu, temp, ram, vram):
        # Grabs the exact time right now
        now = datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S")

        # Inserts the new row of data into the database
        self.cursor.execute('''
                            INSERT INTO metrics (timestamp, cpu_load, cpu_temp, ram_usage, vram_clock)
                            VALUES (?, ?, ?, ?, ?)
                            ''', (now, cpu, temp, ram, vram))

        self.conn.commit()
