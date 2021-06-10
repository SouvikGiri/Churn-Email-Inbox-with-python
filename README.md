# Churn-Email-Inbox-with-python
In this project, we will use Python to access the data from files and process it to achieve certain tasks. we will explore the MBox email dataset, and use Python to count lines, headers, subject lines by emails and domains. 

def number_of_lines():
    fhand = open('/cxldata/datasets/project/mbox-short.txt')
    inp = fhand.read()
    fhand.close()
    count = 0
    for c in inp:
        if c == '\n':
            count += 1
    return count
    
   fhand = open('/cxldata/datasets/project/mbox-short.txt')
count = 0
for line in fhand:
    line = line.rstrip() # Remove new line characters from right
    if line.startswith('From:'):
        print(line)
        
def count_number_of_lines():
    with open('/cxldata/datasets/project/mbox-short.txt') as f:
        cnt = 0
        for c in f:
            c=c.rstrip()
            if c.startswith('Subject:'):
                cnt += 1
    return cnt
count_number_of_lines()

def average_spam_confidence():
    f=open("/cxldata/datasets/project/mbox-short.txt","r")
    spam_confidence_sum=0
    count=0
    for line in f:
        line=line.rstrip()
        if(line.startswith("X-DSPAM-Confidence:")):
            var,value=line.split(":")
            spam_confidence_sum=spam_confidence_sum+float(value)
            count=count+1
            var,value="X-DSPAM-Confidence:".split(":")
                print(var)
                print(value)
                
import re
def find_email_sent_days():
    with open("/cxldata/datasets/project/mbox-short.txt") as f:
            content=f.readlines()            
            day_dict={}
            dayofweek=''
            for line in content:
                if re.findall('From ',line):
                    dayofweek=line.split(' ')[2]
       day_dict[dayofweek]= day_dict.get(dayofweek,0) + 1                    
                      return day_dict
                      print(find_email_sent_days())

import re
def count_message_from_email():
    file=input('Enter file Address : ')
    fhandle = open(file)
    dic = {}
    for line in fhandle:
        if line.find('From:')!= -1: 
            emailid = re.findall('\S+.@.+\S' ,line )
            KEY = str(emailid)
            dic[KEY] = dic.get(KEY,0) +1
    return dic

def count_message_from_email():
    lineslist=[]
    emaildict={}
    with open("/cxldata/datasets/project/mbox-short.txt") as f:
      for line in f:
        lineslist = line.split()
        if line.startswith('From:'):
          email=lineslist[1]
          if email not in emaildict:
            emaildict[email] = 1
          else:
            emaildict[email] += 1
    return emaildict
   
  def count_message_from_domain():
    lineslist=[]
    domaindict={}
    with open("/cxldata/datasets/project/mbox-short.txt") as f:
        for line in f:
            lineslist = line.split()
            if line.startswith('From:'):
                email=lineslist[1]
                domain = email.split('@')[1] 
                if domain not in domaindict:
                    domaindict[domain] = 1
                else:
                    domaindict[domain] += 1
    return domaindict

