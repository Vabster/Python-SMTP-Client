import smtplib
from email.mime.text import MIMEText
# Connects to the SMTP server
socket = smtplib.SMTP('localhost')
# Lets user know a connection to the server has been made
print "Connected to SMTP Server at " + socket.local_hostname
# Sets emailFrom to nike address
emailFrom = "dillon@nike.cs.uga.edu"
# Tells user where message will be sent from
print "Sending mail from: " + emailFrom

# Prompts the user for the recipient of the email
emailTo = raw_input("Recipient: ")
# Prompts the user for the subject of the message
subject = raw_input("Subject: ")
# Prompts the user for the contents of the message
print "Enter message, terminated by <newline>.<newline> "

# Initializes the message to blank string
msg = ""
while 1:
    """
    Gets a line from the client and adds it to the msg.
    Ends loop if a line only contains a single .
    """
    try:
        input = raw_input()
        # Breaks if line from user is .
        if input == ".":
            break
        msg = msg + input + "\n"
    except:
        break

# Sets the message content
msg = MIMEText(msg)
# Sets the content of the subject
msg['Subject'] = subject
# Sets where message is sent from
msg['From'] = emailFrom
# Sets where the message goes to
msg['To'] = emailTo

# Checks if server accepts the recipient address. Let's user know outcome
try:
    # Sends the message through the SMTP server
    socket.sendmail(emailFrom, [emailTo], msg.as_string())
    print "Message sent!"
    # Let's user know that connection to server is over
    print "Thanks for using this SMTP Client! Bye!"
except:
    # Tells user the recipient address has been refused
    print "The recipient has been refused by the server. Sorry. Connection Closing"
# Ends connection with server
# try/except added because random error occurred during one run, due to the socket.quit() line
try:
    socket.quit()
except:
    print "Socket Closed"


