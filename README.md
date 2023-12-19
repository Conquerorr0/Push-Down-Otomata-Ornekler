# Push-Down-Otomata-Ornekler

## Pushdown Otomatonu (PDA) Açıklaması

Bu Java programı, aşağıdaki dilin kabul edilip edilmediğini kontrol etmek için bir Yığıt Otomatonu'nu (Pushdown Automaton - PDA) uygular:

### Dil
L={a^nb^2n ∣ a,b≥1}
Bu dildeki kelimeler, a harflerinin b harflerinin tam olarak iki katı olduğu tüm kombinasyonları içerir. Örneğin "aabbbb", "aaabbbbbb" gibi kelimeler dilin bir parçasıdır, ancak "abbb", "aab" gibi kelimeler değildir.

### Yığıt Otomatonu Kuralları

- **Alfabe:**
  - İki sembol: 'a' ve 'b'
- **Durumlar:**
  - Q0, Q1, Q2
- **Başlangıç Durumu:**
  - Q0
- **Bitiş Durumu:**
  - Q2

### Yığıt Otomatonu Kuralları
- **Q0 Durumu:**
  - Her 'a' karakteri için iki 'X' karakteri yığıta eklenir ve Q1 durumuna geçilir.
- **Q1 Durumu:**
  - Her 'a' için yığıta iki 'X' eklenir.
  - Her 'b' için, yığıtın tepesinde 'X' varsa bir 'X' çıkarılır ve Q2 durumuna geçilir.
- **Q2 Durumu:**
  - Her 'b' için, yığıtın tepesinde 'X' varsa bir 'X' çıkarılır.

### Programın İşleyişi
- Kullanıcıdan bir kelime istenir ve büyük harfe dönüştürülür.
- Her bir karakter kontrol edilir ve belirtilen kurallara göre durumlar güncellenir ve yığıt işlemi yapılır.
- Eğer girilen kelime dilin kurallarına uymuyorsa veya yığıtın sonunda hala eleman varsa, kelime dilin bir parçası olarak kabul edilmez.
- Eğer girilen kelime dilin yapılandırmasına uyuyorsa ve yığıt boş ise, kelime dilin bir parçası olarak kabul edilir.

