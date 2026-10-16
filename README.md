import threading
import time

class BCM:
    def __init__(self):
        self.voltage = 0
        self.BCM_temperature = 0
        time.sleep(1)
    def Monitor_Can_message(self,CAN_ID,CAN_Data):
        for i in range(6):
            self.CAN_ID = CAN_ID
            self.CAN_Data = CAN_Data
            print(f"CAN thread: Monitoring CAN messages-CAN ID = {CAN_ID}, CAN Data = {CAN_Data} ")
        time.sleep(2)
    def Monitor_voltage(self,Voltage):
        for i in range(6):
            self.Voltage = Voltage
            if Voltage>=11:
                print("Voltage thread: Voltage =",Voltage)
            else:
                print("Voltage thread: Error - Low Voltage")
            time.sleep(3)
    def Monitor_temperature(self, Temp):
        self.Temp = Temp
        for i in range(6):
            if Temp<=80:
                print("Temperature thread : Temperature =",Temp,"celsius")
            else:
                print("Temperature thread: Error- High Temperature")
    def Diagnostic_Test(self):
        for i in range(6):
            print("Diagnostic: starting Test")
            time.sleep(1)
            print("Diagnostic : sending Request")
            time.sleep(1)
            print("Diagnostic:waiting for response")
            time.sleep(1)
            print("Diagnostic: Test completed")
bcm = BCM()
CAN_ID =int(input("Enter the CAN_ID: "))
CAN_Data = input("Enter the CAN DATA: ")
Voltage = int(input("Enter the BCM voltage: "))
Temp = int(input("Enter the temperature: "))

thread1 = threading. Thread(target=bcm.Monitor_Can_message,args=(CAN_ID,CAN_Data))
thread2 = threading.Thread(target=bcm.Monitor_voltage,args=(Voltage,))
thread3 = threading.Thread(target =bcm.Monitor_temperature,args =(Temp,))
thread4 = threading.Thread(target =bcm.Diagnostic_Test)

print("______________BCM Test started________________")

thread1.start()
thread2.start()
thread3.start()
thread4.start()

thread1.join()
thread2.join()
thread3.join()
thread4.join()

print("_______________Test is completed_______________")
