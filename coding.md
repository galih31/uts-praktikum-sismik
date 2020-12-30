;# uts-praktikum-sismik
;alarm anti maling denga ic89c51 dan push off button sebagai sensor pada pintu dan jendela
;alarm anti maling

ORG 00H ;awal program

START:
   MOV A,#07FH ; mengisi akumulator dengan data 7FH
   
PUTAR:
   MOV P0,A ;menyalin data dari akumulator ke p0
   RR A ;memutar 1 bit data ke kanan
   ACALL TUNDA ;memanggil subturbin tunda untuk waktu tunda penyalaan
   SJMP PUTAR ; lompat ke label mulai secara berulang
   
TUNDA:
   MOV R5,#250 ;mengisi register 5 dengan data 250
TUNDA1:
   MOV R6,#100 ; mengisi register 6 dengan data 100
TUNDA2:
   MOV R7,#10 ; megisi register 7 dengan data 10
   DJNZ R7,$ ; kurangi R7 dengan 1 sampai 0
   DJNZ R6,TUNDA2 ;kurangi R6 jika belum 0 lompat ke TUNDA2
   DJNZ R5,TUNDA1 ;kurangi R7 jika belum 0 lompat ke TUNDA1
   RET ;kembali ke program utama
   END
