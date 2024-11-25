# Ürünler Arası Kosinüs Benzerliği Hesaplama

Bu projede, üç ürün arasındaki kosinüs benzerliğini hesaplayan bir R kodu bulunmaktadır.

## Kullanılan Vektörler

- **Ürün 1**: `(2, 10, 25)`
- **Ürün 2**: `(4, 55, 12)`
- **Ürün 3**: `(250, 1500, 7500)`

## Kosinüs Benzerliği Hesaplama

Aşağıda, verilen ürünlerin kosinüs benzerliğini hesaplamak için kullanılan R kodu bulunmaktadır.

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
