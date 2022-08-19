# gender22
!git clone https://github.com/NickShin22/22data
!apt-get install fonts-nanum -qq > /dev/null
!fc-cache -fv
import matplotlib as mpl
mpl.font_manager._rebuild()
findfont = mpl.font_manager.fontManager.findfont
mpl.font_manager.findfont = findfont
mpl.backends.backend_agg.findfont = findfont
import matplotlib.pyplot as plt
plt.rc('font', family = 'NanumGothic')
plt.rcParams['axes.unicode_minus'] = False
plt.title('한글제목')
plt.plot([-1,0,1])
plt.show()
import csv
f = open('gender2022.csv')
data = csv.reader(f)

m = []
f = []
name = input('남녀 성비 구성을 찾고 싶은 지역의 이름을 알려주세요 :')

for row in data :
    if name in row[0] :
      for i in range(3, 104) : 
        m.append(int(row[i]))
        f.append(int(row[i+103]))
      break

import matplotlib.pyplot as plt
plt.plot(m, label = 'male')
plt.plot(f, label = 'female') 
plt.legend()
plt.show()
