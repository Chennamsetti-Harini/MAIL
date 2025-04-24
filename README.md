import smtplib
import random
from email.mime.multipart import MIMEMultipart
from email.mime.text import MIMEText

otp=random.randint(1111,9999)
body=f"OTP VALIDATION IS {otp}"

msg=MIMEMultipart()
msg["From"] = "harinich966@gmail.com"
msg["To"] = input("Enter Mail Id:")
msg["Subject"] ="OTP Validation"
msg.attach(MIMEText(body,'plain'))

server = smtplib.SMTP("smtp.gmail.com",587)
server.starttls()
server.login("harinich966@gmail.com","zsjc yfhk sarg mvid")
server.send_message(msg)
server.quit()

cotp = int(input("Enter OTP Received: "))
if otp == cotp:
    print("otp verification success")
else:
    print("invalid otp")
