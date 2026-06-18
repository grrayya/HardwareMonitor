import psutil
import random

class HardwareSensors:
    def get_cpu_usage(self):
        # Asks the CPU how hard it is working (returns a percentage)
        return psutil.cpu_percent(interval=0.1)

    def get_cpu_temp(self):
        # Hardware temps can be tricky to read without admin rights,
        # so we will use a fallback just in case it fails.
        try:
            temps = psutil.sensors_temperatures()
            # Grabs the coretemp if available
            if 'coretemp' in temps:
                return round(temps['coretemp'][0].current)
            return 45 # Default fallback temp
        except Exception:
            return 45

    def get_ram_usage(self):
        # Checks how much memory is currently being used
        return psutil.virtual_memory().percent

    def get_vram_clock_sim(self):
        # Simulating a GPU VRAM clock speed between 800 and 1200 MHz
        # (Reading real GPU data requires much heavier libraries!)
        return random.randint(800, 1200)
