# Ürünler Arası Kosinüs Benzerliği Hesaplama

Bu projede, üç ürün arasındaki kosinüs benzerliğini hesaplayan bir R kodu bulunmaktadır.

## Kullanılan Vektörler

- **Ürün 1**: `(2, 10, 25)`
- **Ürün 2**: `(4, 55, 12)`
- **Ürün 3**: `(250, 1500, 7500)`

## Kosinüs Benzerliği Hesaplama

Aşağıda, verilen ürünlerin kosinüs benzerliğini hesaplamak için kullanılan R kodu bulunmaktadır.

#**************************************************************************************************************************

# Müşteri Ürün Verileri Arası Kosinüs Benzerliği Hesaplama

Bu projede, bir dizi müşteri ve onların ürünlere olan talepleri arasındaki kosinüs benzerliğini hesaplayan bir R kodu bulunmaktadır.

## Veri Kümesi

Veri kümesinde üç müşteri ve her bir müşteri için üç ürün yer almaktadır. Veri aşağıdaki gibi tanımlanmıştır:

| Müşteri   | Urun_A | Urun_B | Urun_C |
|-----------|--------|--------|--------|
| Müşteri_1 | 1      | 2      | 44     |
| Müşteri_2 | 0      | 4      | 23     |
| Müşteri_3 | 3      | 19     | 15     |

## Kosinüs Benzerliği Hesaplama

Kosinüs benzerliği, iki vektör arasındaki açıyı ölçen bir yöntemdir ve iki örneğin benzerliğini hesaplamak için kullanılır. Bu projede, her müşteri arasındaki benzerlik hesaplanacaktır.

### R Kodu

Aşağıdaki R kodu, müşteri-ürün veri kümesindeki her örnek (müşteri) arasındaki kosinüs benzerliğini hesaplamak için kullanılır.


### R Kodu

```r
# Vektörler
urun_1 <- c(2, 10, 25)
urun_2 <- c(4, 55, 12)
urun_3 <- c(250, 1500, 7500)

# Kosinüs benzerliğini hesaplayan fonksiyon
kosinus_benzerligi <- function(v1, v2) {
  carpimlar <- sum(v1 * v2)  # Skaler çarpım
  norm_v1 <- sqrt(sum(v1^2))  # Vektör 1'in normu
  norm_v2 <- sqrt(sum(v2^2))  # Vektör 2'nin normu
  return(carpimlar / (norm_v1 * norm_v2))  # Kosinüs benzerliği
}

# Hesaplamalar
benzerlik_1_2 <- kosinus_benzerligi(urun_1, urun_2)
benzerlik_1_3 <- kosinus_benzerligi(urun_1, urun_3)
benzerlik_2_3 <- kosinus_benzerligi(urun_2, urun_3)

# Sonuçları yazdırma
cat("Kosinüs Benzerliği (Ürün 1 - Ürün 2):", benzerlik_1_2, "\n")
cat("Kosinüs Benzerliği (Ürün 1 - Ürün 3):", benzerlik_1_3, "\n")
cat("Kosinüs Benzerliği (Ürün 2 - Ürün 3):", benzerlik_2_3, "\n")

##Sonuç:
Kosinüs Benzerliği (Ürün 1 - Ürün 2): 0.5630783 
Kosinüs Benzerliği (Ürün 1 - Ürün 3): 0.9824772 
Kosinüs Benzerliği (Ürün 2 - Ürün 3): 0.4017306

#***********************************************************************

# Veri çerçevesini oluşturma
data <- data.frame(
  Musteriler = c("Müşteri_1", "Müşteri_2", "Müşteri_3"),
  urun_A = c(1, 0, 3),
  urun_B = c(2, 4, 19),
  urun_C = c(44, 23, 15)
)

# Kosinüs benzerliğini hesaplayan fonksiyon
kosinus_benzerligi <- function(v1, v2) {
  dot_product <- sum(v1 * v2)  # Skaler çarpım
  norm_v1 <- sqrt(sum(v1^2))  # Vektör 1'in normu
  norm_v2 <- sqrt(sum(v2^2))  # Vektör 2'nin normu
  return(dot_product / (norm_v1 * norm_v2))  # Kosinüs benzerliği
}

# Kosinüs benzerliği matrisini oluşturma
benzerlik_matrix <- matrix(0, nrow = nrow(data), ncol = nrow(data))
rownames(benzerlik_matrix) <- data$Musteriler
colnames(benzerlik_matrix) <- data$Musteriler

# Her müşteri için benzerlik hesaplama
for (i in 1:nrow(data)) {
  for (j in 1:nrow(data)) {
    if (i != j) {
      benzerlik_matrix[i, j] <- kosinus_benzerligi(as.numeric(data[i, 2:4]), as.numeric(data[j, 2:4]))
    } else {
      benzerlik_matrix[i, j] <- 1  # Kendiyle benzerlik her zaman 1
    }
  }
}

# Benzerlik matrisini yazdırma
print(benzerlik_matrix)



##Sonuç:
          Müşteri_1 Müşteri_2 Müşteri_3
Müşteri_1 1.0000000 0.9917202 0.6522991
Müşteri_2 0.9917202 1.0000000 0.7393079
Müşteri_3 0.6522991 0.7393079 1.0000000
