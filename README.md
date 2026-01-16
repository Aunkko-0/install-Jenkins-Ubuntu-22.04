# install-Jenkins-Ubuntu-22.04
# ทำทีละสเต็ป
1. ติดตั้ง Java (OpenJDK) Jenkins ทำงานด้วยภาษา Java ดังนั้นจำเป็นต้องติดตั้ง Java
```
sudo apt update && sudo apt upgrade -y
sudo apt install openjdk-21-jre -y
java -version
```
2. เพิ่ม Repository และ Authentication Key ของ Jenkins
```
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
    https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
    https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
    /etc/apt/sources.list.d/jenkins.list > /dev/null
```
3. อัพเดทก่อนติดตั้ง Jenkins 
```
sudo apt update -y
```
4. ติดตั้ง Jenkins รอจนกว่าจะติดตั้งเสร็จ
```
sudo apt install jenkins -y
```
5. ตรวจสอบสถานะและเริ่มใช้งานของ Jenkins
```
systemctl status jenkins
sudo systemctl enable jenkins
```
6. เปิด Firewall ให้สถานะ Active
```
sudo ufw allow 8080
sudo ufw status
```
ถ้าสถานะขึ้น inactive ให้ใช้คำสั่ง
```
sudo ufw enable
```
7. ใช้งาน jenkins บน Browser
```
http://localhost:8080 // http://ip_address_or_domain:8080
```
8. ตัว Jenkins ต้องการ initialAdminPassword เพื่อยืนยันเข้าใช้งาน
```
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
ให้ Copy แล้วเอากรอกในช่องว่าง 

Credit: (https://medium.com/@ranjith_99360/how-to-install-jenkins-on-ubuntu-22-04-17b99fd41678)
