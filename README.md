# Pump_Sizing
This Python script helps users select the appropriate pump type based on their flow rate, pressure, and other requirements. It follows a structured decision tree inspired by an industrial pump selection flowchart.
# Pump Selection Tool

This Python script helps users select the appropriate pump type based on their flow rate, pressure, and other requirements. It follows a structured decision tree inspired by an industrial pump selection flowchart.

## How It Works
- The script prompts users to input their flow rate in GPM.
- Based on the flow rate, it asks additional questions regarding pressure, particulate matter, self-priming capability, and other factors.
- After gathering the necessary inputs, it determines and prints the most suitable pump type.

## Usage
Run the script in a Python environment:
```sh
python pump_selection.py
```
Follow the prompts to receive the recommended pump type.

## Requirements
- Python 3.x

## License
This project is open-source and available for use under the MIT License.

---

def select_pump():
    flow_rate = float(input("Enter flow rate (GPM): "))
    if flow_rate < 1:
        pressure = float(input("Enter pressure (PSI): "))
        if pressure < 30:
            pulseless = input("Do you require a pulseless flow? (yes/no): ").strip().lower()
            if pulseless == "yes":
                return "Peristaltic (tubing) or Progressing Cavity"
            else:
                return "Double-Diaphragm"
        else:
            particulate = input("Does your fluid contain particulate matter? (yes/no): ").strip().lower()
            if particulate == "yes":
                return "Double-Diaphragm"
            else:
                return "Diaphragm (metering) or Peristaltic (tubing)"
    elif 1 <= flow_rate <= 20:
        pressure = float(input("Enter pressure (PSI): "))
        if pressure < 30:
            self_priming = input("Do you require a self-priming pump? (yes/no): ").strip().lower()
            if self_priming == "yes":
                return "Flexible Impeller or Peristaltic (tubing)"
            else:
                return "Centrifugal or Gear"
        else:
            return "Gear, Pressure Washer, Progressing Cavity, or Rotary Lobe"
    else:
        pressure = float(input("Enter pressure (PSI): "))
        if pressure < 30:
            return "Centrifugal"
        else:
            particulate = input("Does your fluid contain particulate matter? (yes/no): ").strip().lower()
            if particulate == "yes":
                return "Double-Diaphragm"
            else:
                return "Centrifugal, Gear, Progressing Cavity, or Rotary Vane"

if __name__ == "__main__":
    pump_type = select_pump()
    print(f"Recommended Pump Type: {pump_type}")
