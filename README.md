import random

print('=====  QUIZ  =====')

print('\nJenis Kuis: \n'.upper())
print('- Matematika\n- Bahasa Inggris\n- IPA\n- Umum \n'.upper())
bab = input('Pilih salah satu: '.upper()).lower()
print('='*40)
print('')
print('           kuis'.upper(), bab.upper())
print('')
print('')

if bab == 'matematika':
    skor = 0
    for i in range(5):
        num1 = random.randint(1, 100)
        num2 = random.randint(1, 100)
        sign = random.choice(['-', '+', 'x', ':'])

        if sign == '-':
            true = num1 - num2
        elif sign == '+':
            true = num1 + num2
        elif sign == 'x':
            true = num1 * num2
        else:
            true = round(num1 / num2, 2)

        pil1 = true - random.randint(1, 5)
        pil2 = true + random.randint(1, 5)
        pil = [pil1, pil2, true]
        random.shuffle(pil)
        
        print(num1, sign, num2, '= ')
        print('')
        print('A.', pil[0])
        print('B.', pil[1])
        print('C.', pil[2])
        print('')

        jawab = input('Jawaban: ').lower()

        if jawab == 'a' and pil[0] == true:
            print('Betul')
            print('')
            print('='*30)
            skor += 20
        elif jawab == 'b' and pil[1] == true:
            print('Betul')
            print('')
            print('='*30)
            skor += 20
        elif jawab == 'c' and pil[2] == true:
            print('Betul')
            print('')
            print('='*30)
            skor += 20
        else:
            print('Salah')
            print('='*30)
            print('')
    print('\nSkor akhir kamu:', skor)

#####################################

elif bab == 'bahasa inggris':
    skor = 0
    quest1 = 'Choose the correct sentence:'
    quest2 = 'What is the synonym of the word "happy"?'
    quest3 = 'Complete the sentence: My brother ___ to school every day.'
    quest4 = 'Which one is a plural noun?'
    quest5 = 'Choose the correct translation: "Saya sedang membaca buku."'
    quests = [quest1, quest2, quest3, quest4, quest5]

    for i in range(5):
        quest = random.choice(quests)
        quests.remove(quest)
        
        if quest == quest1:
            pil1 = "She don't like coffee."
            pil2 = "She doesn't likes coffee."
            pil3 = "She don't likes coffee."
            true = "She doesn't like coffee."
        
        elif quest == quest2:
            pil1 = "Angry."
            pil2 = "Sad."
            pil3 = "Tired."
            true = "Joyful."
        
        elif quest == quest3:
            pil1 = "Gone"
            pil2 = "Going"
            pil3 = "Go"
            true = "Goes"
        
        elif quest == quest4:
            pil1 = "Cat."
            pil2 = "Child."
            pil3 = "Man."
            true = "Books."
        
        else:
            pil1 = "I was read a book"
            pil2 = "I read a book."
            pil3 = "I reads a book."
            true = "I am reading a book"
        
        pil = [pil1, pil2, pil3, true]    
        random.shuffle(pil)
            
        print(quest)
        print('')
        print('A.', pil[0])
        print('B.', pil[1])
        print('C.', pil[2])
        print('D.', pil[3])
        print('')
        jawab = input('Jawaban: ').lower()
        
        if jawab == 'a' and pil[0] == true:
            print('Betul')
            print('')
            print('='*30)
            skor += 20
        elif jawab == 'b' and pil[1] == true:
            print('Betul')
            print('')
            print('='*30)
            skor += 20
        elif jawab == 'c' and pil[2] == true:
            print('Betul')
            print('')
            print('='*30)
            skor += 20
        elif jawab == 'd' and pil[3] == true:
            print('Betul')
            print('')
            print('='*30)
            skor += 20
        else:
            print('Salah')
            print('')
            print('='*30)
    
    print('skor =', skor)
    
##########################################

elif bab == 'ipa':
    skor = 0
    quest1 = 'Apa fungsi utama akar pada tumbuhan?'
    quest2 = 'Benda yang dapat menghantarkan listrik disebut...?'
    quest3 = 'Air berubah menjadi uap disebut proses...?'
    quest4 = 'Planet terdekat dengan Matahari adalah...?'
    quest5 = 'Bagian tubuh manusia yang berfungsi memompa darah adalah...?'
    quests = [quest1, quest2, quest3, quest4, quest5]

    for i in range(5):
        quest = random.choice(quests)
        quests.remove(quest)
        
        if quest == quest1:
            pil1 = "melakukan fotosintesis.".capitalize()
            pil2 = "mengatur suhu tubuh.".capitalize()
            pil3 = "menghasilkan buah.".capitalize()
            true = "menyerap air dan mineral.".capitalize()
        
        elif quest == quest2:
            pil1 = "kayu.".capitalize()
            pil2 = "plastik.".capitalize()
            pil3 = "karet.".capitalize()
            true = "logam.".capitalize()
        
        elif quest == quest3:
            pil1 = "membeku".capitalize()
            pil2 = "mencair".capitalize()
            pil3 = "mengembun".capitalize()
            true = "menguap".capitalize()
        
        elif quest == quest4:
            pil1 = "mars.".capitalize()
            pil2 = "bumi.".capitalize()
            pil3 = "venus.".capitalize()
            true = "merkurius.".capitalize()
        
        else:
            pil1 = "ginjal".capitalize()
            pil2 = "otak.".capitalize()
            pil3 = "paru-paru.".capitalize()
            true = "jantung.".capitalize()
        
        pil = [pil1, pil2, pil3, true]    
        random.shuffle(pil)
            
        print(quest)
        print('')
        print('A.', pil[0])
        print('B.', pil[1])
        print('C.', pil[2])
        print('D.', pil[3])
        print('')
        jawab = input('Jawaban: ').lower()
        
        if jawab == 'a' and pil[0] == true:
            print('Betul')
            print('')
            print('='*30)
            skor += 20
        elif jawab == 'b' and pil[1] == true:
            print('Betul')
            print('')
            print('='*30)
            skor += 20
        elif jawab == 'c' and pil[2] == true:
            print('Betul')
            print('')
            print('='*30)
            skor += 20
        elif jawab == 'd' and pil[3] == true:
            print('Betul')
            print('')
            print('='*30)
            skor += 20
        else:
            print('Salah')
            print('')
            print('='*30)
    
    print('skor =', skor)
    
##########################################

elif bab == 'umum':
    skor = 0
    quest1 = 'Lagu kebangsaan Indonesia diciptakan oleh...'
    quest2 = 'Sungai terpanjang di dunia adalah...'
    quest3 = 'Perangkat keras komputer yang berfungsi menampilkan hasil pemrosesan data ke pengguna adalah...'
    quest4 = 'Negara dengan jumlah penduduk terbanyak di dunia adalah...'
    quest5 = 'Zat yang digunakan tanaman dalam proses fotosintesis untuk menangkap cahaya matahari adalah...'
    quests = [quest1, quest2, quest3, quest4, quest5]

    for i in range(5):
        quest = random.choice(quests)
        quests.remove(quest)
        
        if quest == quest1:
            pil1 = "H. Mutahar.".capitalize()
            pil2 = "Ismaul Marzuki.".capitalize()
            pil3 = "Ibu Sud.".capitalize()
            true = "Wage Rudolf Supratman".capitalize()
        
        elif quest == quest2:
            pil1 = "Yangtze.".capitalize()
            pil2 = "Mississippi.".capitalize()
            pil3 = "Amazon.".capitalize()
            true = "Nil.".capitalize()
        
        elif quest == quest3:
            pil1 = "Mouse".capitalize()
            pil2 = "Printer".capitalize()
            pil3 = "CPU".capitalize()
            true = "Monitor".capitalize()
        
        elif quest == quest4:
            pil1 = "Amerika Serikat.".capitalize()
            pil2 = "Indonesia.".capitalize()
            pil3 = "Tiongkok.".capitalize()
            true = "India.".capitalize()
        
        else:
            pil1 = "Oksigen".capitalize()
            pil2 = "Karbondioksida.".capitalize()
            pil3 = "Glukosa".capitalize()
            true = "Klorofil.".capitalize()
        
        pil = [pil1, pil2, pil3, true]    
        random.shuffle(pil)
            
        print(quest)
        print('')
        print('A.', pil[0])
        print('B.', pil[1])
        print('C.', pil[2])
        print('D.', pil[3])
        print('')
        jawab = input('Jawaban: ').lower()
        
        if jawab == 'a' and pil[0] == true:
            print('Betul')
            print('')
            print('='*30)
            skor += 20
        elif jawab == 'b' and pil[1] == true:
            print('Betul')
            print('')
            print('='*30)
            skor += 20
        elif jawab == 'c' and pil[2] == true:
            print('Betul')
            print('')
            print('='*30)
            skor += 20
        elif jawab == 'd' and pil[3] == true:
            print('Betul')
            print('')
            print('='*30)
            skor += 20
        else:
            print('Salah')
            print('')
            print('='*30)
    
    print('skor =', skor)
    
##################################
else:
      print('Kuis belum tersedia'.upper())
      print('KUIS YANG TERSEDIA'.upper())
      print('- Matematika\n- Bahasa Inggris\n- IPA\n- Umum \n'.upper())
