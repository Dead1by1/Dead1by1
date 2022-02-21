# Script programa para enviar correos

import smtplib
import getpass
import ssl

# Aqui se formula la seccioón encargada del nombre de usuario y contraseña
username = input("Ingrese su nombre de usuario:")
password = getpass.getpass ("Ingrese su password")

# Aquí se formula la parte encargada de conectar con el servidor SMTP y de los datos de creación del correo electronico
context = ssl.create_default_context()


with smtplib.SMTP_SSL("smtp.gmail.com", 465, context=context) as server:
     server.login(username, password)
     print("Inició sesión")
     destinatario = input("Ingrese el destinatario: ")
     mensaje = input("Ingrese el mensaje: ")
     server.sendmail(username, destinatario, mensaje)
     print("Mensaje enviado")
