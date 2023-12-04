import re

phone = input('Введите номер телефона ')
print('phone #', phone, type(phone))

if re.fullmatch(r'^((8|\+7)[\- ]?)?(\(?\d{3}\)?[\- ]?)?[\d\- ]{7,10}$', phone):
    print('Номер корректен')
else:
    print('Некорректный номер телефона')

phone_book = [phone, '8(495)430-23-97', '+7-4-95-43-023-97',
              '4-3-0-2-3-9-7', '8(918)523-84-95', '8-496-430']
print('phone_book # \t', phone_book, type(phone_book))

phone_book_new = [s.replace('-', '').replace(' ', '').replace('(', '').replace(')', '')
                  for s in phone_book]

for i in range(len(phone_book_new)):
    if len(phone_book_new[i])==7:
        phone_book_new[i] += '+7495'
    elif phone_book_new[i][0] == '8':
        phone_book_new[i] = '+7' + phone_book_new[i][1:]
    elif len(phone_book_new[i])==9:
        phone_book_new[i] = '+7'+phone_book_new[i]
print('phone_book_new', phone_book_new, type(phone_book_new))

for i in range(1, len(phone_book_new)):
    if phone_book_new[0] == phone_book_new[i]:
        print('YES')
    else:
        print('NO')
