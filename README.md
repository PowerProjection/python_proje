# SORU 1: 
### Bir listeyi düzleştiren (flatten) fonksiyon yazın. Elemanları birden çok katmanlı listelerden ([[3],2] gibi) oluşabileceği gibi, non-scalar verilerden de oluşabilir. Örnek olarak:
input: `[[1,'a',['cat'],2],[[[3]],'dog'],4,5]`

output: `[1,'a','cat',2,3,'dog',4,5]`

### Birinci soruda ilk önce eskiden beri bildiğim gibi problemi if-else kullanarak çözmeye çalıştım ve kod bu şekilde oldu:
# SORU 1 - ÇÖZÜM 1:
	def flatten(x):
	    string = ""
	    for i in x:
	        if type(i) == list:
	            for e in i:
	                if type(e) == list:
	                    for k in e:
	                        if type(k) == list:
	                            for z in k:
	                                string += str(z) + " "
	                        else: 
	                            string += str(k) + " "
	                else:
	                    string += str(e) + " "
	        else:
	            string += str(i) + " "
	    print(string)
	    
	input= [[1,'a',['cat'],2],[[[3]],'dog'],4,5]
    flatten(input)
  
OUTPUT>>>:	`1 a cat 2 3 dog 4 5`

### Bu kodla sonuç aldım fakat kodun çok karmaşık olduğunu ve katman sayısı arttıkça bu kodun çalışmayacağını ayrıca çıkan sonucun string olmaması gerektiğini düşündüğümden bu fonksiyonu recursive şekilde tekrar kodlamam gerektiğine karar verdim.
# SORU 1 - ÇÖZÜM 2:
	d = []
	def flatten(x):
	    for i in x:
	        if type(i) == list:
	            flatten(i)
	        else:
	            d.append(i)
	            
	input= [[1,'a',['cat'],2],[[[3]],'dog'],4,5]
	flatten(input)
	print(d)

OUTPUT>>>:	 `[1,'a','cat',2,3,'dog',4,5]`

### Yukarıdaki fonksiyonu yazdıktan sonra if-else ile yazdığım kodun ne kadar amatörce olduğunun farkına vardım :)
# # #
# SORU 2:
### Verilen listenin içindeki elemanları tersine döndüren bir fonksiyon yazın. Eğer listenin içindeki elemanlar da liste içeriyorsa onların elemanlarını da tersine döndürün. Örnek olarak:
input: `[[1, 2], [3, 4], [5, 6, 7]]`

output: `[[[7, 6, 5], [4, 3], [2, 1]]`

# SORU 2 ÇÖZÜM:
	r = []
	def reverse(x):
	   x = x[::-1]
	   r = x
	   for i in range(len(x)):
	       x[i] = x[i][::-1]
	   return r
	
	input = [[1, 2], [3, 4], [5, 6, 7]]
	reverse(input)

OUTPUT>>>: 	[[7, 6, 5], [4, 3], [2, 1]]
