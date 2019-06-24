import serial
import serial.tools.list_ports
import time
import binascii
'''シリアル通信でデータの送受信を行う'''

'''Main関数'''
if __name__ == '__main__':
    
    ser = serial.Serial('COM5', 115200, bytesize=8, timeout = 0.01)  # timeoutを秒で設定（default:None)ボーレートはデフォルトで9600
    print("sireal is already confirmed")
    
    motor_angle = 0
    max_angle = 600
    print("Hello")
    for num_of_swing in range(100):
        for x in range(3000):
                
            ser.write("xyr".encode('utf-8') + str(motor_angle).encode('utf-8') + "\r\n".encode('utf-8'))
            
            line8 = ser.read(size=1000)
            print(line8)
            
            
            if num_of_swing % 2 == 0: 
                motor_angle = motor_angle + 10
            
            else:
                motor_angle = motor_angle - 10
            if motor_angle > max_angle or motor_angle <= 0:
                break
                ser.write("y".encode('utf-8'))
            time.sleep(0.1)
        time.sleep(1)
        
        print("change direction")

    ser.write("p".encode('utf-8'))
    
         
    FinishP = ser.readline()
    print(FinishP)
 
    ser.write("n".encode('utf-8'))

    ser.close()
