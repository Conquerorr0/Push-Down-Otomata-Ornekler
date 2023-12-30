# Push-Down-Otomata-Ornekler

# Örnek 1:

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

## Kod:

    import java.util.Scanner;
    import java.util.Stack;
    
    public class Q1 {
  
      public static void main(String[] args) {
          Scanner scanner = new Scanner(System.in);
          Stack<Character> stack = new Stack<>();
          final STATES FINAL_STATE = STATES.Q2;
          STATES state = STATES.Q0;
  
          System.out.print("Kelime: ");
          String word = scanner.next().toUpperCase();
  
          for (int i = 0; i < word.length(); i++) {
              char letter = word.charAt(i);
  
              if (letter != 'A' && letter != 'B') {
                  System.out.println("Hatali karakter!");
                  System.exit(0);
              }
  
              if (state == STATES.Q0) {
                  if (letter == 'A') {
                      stack.push('X');
                      stack.push('X');
                      state = STATES.Q1;
                  } else {
                      System.out.println(word + " kelimesi otomata tarafindan taninmaz.");
                      System.exit(0);
                  }
              } else if (state == STATES.Q1) {
                  if (letter == 'A') {
                      stack.push('X');
                      stack.push('X');
                  } else if (letter == 'B' && !stack.isEmpty() && stack.peek() == 'X') {
                      stack.pop();
                      state = STATES.Q2;
                  } else {
                      System.out.println(word + " kelimesi otomata tarafindan taninmaz.");
                      System.exit(0);
                  }
              } else if (state == STATES.Q2) {
                  if (letter == 'B' && !stack.isEmpty() && stack.peek() == 'X') {
                      stack.pop();
                  } else {
                      System.out.println(word + " kelimesi otomata tarafindan taninmaz.");
                      System.exit(0);
                  }
              }
          }
  
          if (state == FINAL_STATE && stack.isEmpty()) {
              System.out.println(word + " kelimesi otomata tarafindan taninir.");
          } else {
              System.out.println(word + " kelimesi otomata tarafindan taninmaz.");
          }
      }
    }
    
    enum STATES {
        Q0,
        Q1,
        Q2
    }



    
# Örnek 2:

### Dil ve Yığıt Otomatonu Tanımı

**Dil:**  
$L = \{a^n b^{2n} \mid a, b \geq 1\}$

Bu dil, 'a' harflerinin 'b' harflerinin tam olarak iki katı olduğu tüm kombinasyonları içerir. Örneğin "aabbbb", "aaabbbbbb" gibi kelimeler dilin bir parçasıdır, ancak "abbb", "aab" gibi kelimeler değildir.

**Yığıt Otomatonu Kuralları:**  
- **Alfabe:** İki sembol: 'a' ve 'b'
- **Durumlar:** Q0, Q1, Q2
- **Başlangıç Durumu:** Q0
- **Bitiş Durumu:** Q2

#### Yığıt Otomatonu Kuralları

**Q0 Durumu:**  
Her 'a' karakteri için iki 'X' karakteri yığıta eklenir ve Q1 durumuna geçilir.

**Q1 Durumu:**  
- Her 'a' için yığıta iki 'X' eklenir.
- Her 'b' için, yığıtın tepesinde 'X' varsa bir 'X' çıkarılır ve Q2 durumuna geçilir.

**Q2 Durumu:**  
Her 'b' için, yığıtın tepesinde 'X' varsa bir 'X' çıkarılır.

### Programın İşleyişi

1. Kullanıcıdan bir kelime istenir ve büyük harfe dönüştürülür.
2. Her bir karakter kontrol edilir ve belirtilen kurallara göre durumlar güncellenir ve yığıt işlemi yapılır.
3. Eğer girilen kelime dilin kurallarına uymuyorsa veya yığıtın sonunda hala eleman varsa, kelime dilin bir parçası olarak kabul edilmez.
4. Eğer girilen kelime dilin yapılandırmasına uyuyorsa ve yığıt boş ise, kelime dilin bir parçası olarak kabul edilir.

### Kod Açıklaması

Bu Java kodu, kullanıcının girdiği bir kelimenin verilen dilde olup olmadığını kontrol eder.

- `enum STATES` ve `enum CHARS`, durumları ve karakterleri temsil eder.
- `main` fonksiyonu, kullanıcıdan bir kelime alır ve kurallara göre dilin parçası olup olmadığını kontrol eder.
- Her karakter, belirli durumlar altında kontrol edilir ve yığıt işlemleri yapılır.
- Eğer kelime dilin yapısına uymuyorsa veya yığıt boş değilse, kelime dilin bir parçası olarak kabul edilmez.


## Kod:  
  import java.util.Scanner;
  import java.util.Stack;
  
  
  public class Q2 {
      
      // L = {a^n + b^m + c^k | n >= 1, m >= 2, k >= 1, m = n + k}
      public static void main(String[] args) {
          Scanner scanner = new Scanner(System.in);
          System.out.print("Kelime: ");
          String word = scanner.next();
          
          final STATES FINAL_STATE = STATES.D;
          STATES state = STATES.A;
          
          Stack<CHARS> stack = new Stack<>();
          
          char ch;
          
          for (int i = 0; i < word.length(); i++) {
              ch = word.charAt(i);
              
              if(ch != 'a' && ch != 'b' && ch != 'c'){
                  System.out.println("Hatali karakter!");
                  System.exit(0);
              }
              
              if(state == STATES.A){
                  if(ch == 'a' && stack.isEmpty()){
                      stack.push(CHARS.X);
                      state = STATES.B;
                  }
                  else{
                      System.out.println(word + " otomata tarafindan taninmaz!");
                      System.exit(0);
                  }
              }
              else if(state == STATES.B){
                  if(ch == 'a'){
                      stack.push(CHARS.X);
                      state = STATES.B;
                  }
                  else if(ch == 'b' && !stack.isEmpty() && stack.peek() == CHARS.X){
                      stack.pop();
                      state = STATES.B;
                  }
                  else{
                      state = STATES.C;
                      i--;
                      continue;
                  }
              }
              else if(state == STATES.C){
                  if(ch == 'b'){
                      stack.push(CHARS.Y);
                      state = STATES.C;
                  }
                  else if(ch == 'c' && !stack.isEmpty()){
                      stack.pop();
                      state = STATES.D;
                  }
                  else{
                      System.out.println(word + " otomata tarafindan taninmaz!");
                      System.exit(0);
                  }
              }
              else if(state == STATES.D){
                  if(ch == 'c' && !stack.isEmpty()){
                      stack.pop();
                      state = STATES.D;
                  }
              }
          }
          
          if(state == FINAL_STATE && stack.isEmpty()){
              System.out.println(word + " otomata tarafindan taninir.");
          }
          else{
              System.out.println(word + " otomata tarafindan taninmaz!");
          }
      }
  }
  
  enum STATES{
      A,
      B,
      C,
      D
  }
  
  enum CHARS{
      X,
      Y
  }

