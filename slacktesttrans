import os
import pandas as pd
from google.cloud import translate

os.environ['GOOGLE_APPLICATION_CREDENTIALS'] = 'myproject.json'

print(os.environ.get('GOOGLE_APPLICATION_CREDENTIALS'))


def trans(text, target='en'):
    # class
    translate_client = translate.Client()
    # translation start
    translation = translate_client.translate(
        text,
        target_language=target)

    # 번역전 문자열
    print(u'Text: {}'.format(text))
    # 번역 후 문자열
    print(u'Translation: {}'.format(translation['translatedText']))

    # 번역한 문자열 리턴
    return translation['translatedText']

'''
data = pd.read_excel('olist.xlsx', index_col=None, header=None)
print(data.index)

for row in data.index:
    chText = str(data.loc[row, 1]).strip()
    if chText != 'nan':
        print(data.loc[row, 1])
        trans_text = trans(chText)
        data.loc[row, 1] = trans_text
'''

data = pd.read_csv('olist.csv', index_col=None, header=None)
#print(data)

cnt = 1

for row in range(len(data)):
    chText = str(data.loc[row, 22]).strip()
    if chText != 'nan':
        print(data.loc[row, 22])
        trans_text = trans(chText)
        data.loc[row, 22] = trans_text
    if cnt == 5:
        break
    cnt += 1

data.to_csv('olist_trans.csv')
