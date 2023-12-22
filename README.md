This is a Python phishing tool, it may not work in other software, good use.


import smtplib
from email.mime.text import MIMEText

def send_email(sender_email, sender_password, receiver_email, subject, message):
    try:
        server = smtplib.SMTP('smtp.gmail.com', 587)
        server.starttls()
        server.login(sender_email, sender_password)

        msg = MIMEText(message)
        msg['Subject'] = subject
        msg['From'] = sender_email
        msg['To'] = receiver_email

        server.sendmail(sender_email, receiver_email, msg.as_string())
        server.quit()

        print("Phishing email sent successfully!")
    except Exception as e:
        print("An error occurred while sending the phishing email:", str(e))

sender_email = input("Enter your email address: ")
sender_password = input("Enter your email password: ")
receiver_email = input("Enter the target's email address: ")
subject = input("Enter the subject of the email: ")
message = input("Enter the content of the email: ")

send_email(sender_email, sender_password, receiver_email, subject, message)
