# Age-calculater
from datetime import date
def get_birthdate():
    while True:
        try:
            year=int(input("Enter Year"))
            month=int(input("Enter month"))
            day=int(input("Enter day"))
            
            birthdate=date(year,month,day)
            return birthdate
        except ValueError:
            print("invalid input")

def calculate_age(birthdate):
    today =date.today()
    #age=today-birthdate gives the age in days
    year=today.year-birthdate.year
    month=today.month-birthdate.month
    days=today.day-birthdate.day
    
    if days<0:
        month -=1
        if today.month==1:
            prev_month=12
            prev_year=today.year-1
        else:
            prev_month=today.month-1
            prev_year=today.year
        if today.month==12:
            next_month=1
            next_year=prev_year+1
        else:
            next_month=today.month+1
            next_year=prev_year
            
        days_in_prev_month=(date(next_year,next_month,1)-date(prev_year,prev_month,1))
            
    if today.month<birthdate.month:
        month=(12-birthdate.month)+today.month
        year-=1
    
    else:
        month=today.month-birthdate.month

    return year,month,days


d=get_birthdate()
years,months,days=calculate_age(d)
print(f"you are {years} years,{months} months and {days} days old")
    
    
    
    
    
