# ala
#alarm import time and manage day to day life activity
import time
from datetime import datetime

def set_alarm():
    """Set the alarm time."""
    alarm_time = input("Enter alarm time (format: YYYY-MM-DD HH:MM:SS): ")
    try:
        # Convert the input string to a datetime object
        alarm_time = datetime.strptime(alarm_time, '%Y-%m-%d %H:%M:%S')
        return alarm_time
    except ValueError:
        print("Invalid format. Please use YYYY-MM-DD HH:MM:SS.")
        return set_alarm()

def check_alarm(alarm_time):
    """Check if the current time matches the alarm time."""
    while True:
        current_time = datetime.now()
        if current_time >= alarm_time:
            print("Alarm! It's time!")
            break
        time.sleep(1)  # Sleep for a second before checking again

def main():
    print("Welcome to the Alarm Clock!")
    alarm_time = set_alarm()
    print(f"Alarm set for {alarm_time}.")
    print("Waiting for the alarm...")
    check_alarm(alarm_time)

if __name__ == "__main__":
    main()
