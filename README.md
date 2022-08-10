# converting-pdf-to-speech-
#using python to convert pdf to speech
# use the CMD to install (pip install PyPDF2)
# use the CMD to install (pip install gtts)
# you use pycharm to install the above modules 

import os
import PyPDF2
from gtts import gTTS
from tkinter import Tk
from tkinter.filedialog import askopenfilename

Tk().withdraw()
filelocation = askopenfilename()

with open(filelocation, "rb") as f:
    pdf = PyPDF2.PdfFileReader(f)
    myText = ""
    for pageNum in range(pdf.numPages):
        pageObj = pdf.getPage(pageNum)
        myText += pageObj.extractText()
print(myText)

final_output = gTTS(text=myText, lang='en')
print("Generating.....")
final_output.save("generated_speech.mp3")
os.system("start generated_speech")
print("successfully Generated!!")

