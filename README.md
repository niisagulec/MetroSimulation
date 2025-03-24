# Metro Simülasyonu
Bu proje, bir metro ağında iki istasyon arasındaki en hızlı ve en az aktarmalı rotayı bulmaya yönelik bir uygulamadır. Proje, farklı algoritmalar kullanarak rota bulma işlemi yapar ve gerçek zamanlı metro ağlarında geçerli olabilecek çözümler sunar.

## Kullanılan Teknolojiler & Kütüphaneler

- Python 3: Proje Python 3 ile yazılmıştır. Python’un veri yapıları, algoritmalar ve kütüphaneleri ile hızlı ve verimli bir çözüm sunulmuştur.
- `collections`: Python'un yerleşik kütüphanesinden biri olan `collections`, verimli veri yapıları sağlar. Bu projede `defaultdict` ve `deque` sınıfları kullanılmıştır.
  - `defaultdict`: Anahtarın mevcut olmadığı durumlarda varsayılan bir değer döndüren bir sözlük türüdür. Bu proje, hatlar için kullanılan `defaultdict(list)` veri yapısında istasyonları saklamak için kullanılmıştır.
  - `deque`: İki uçlu kuyruk yapısı sağlar ve özellikle BFS (Breadth-First Search) gibi algoritmalarda kullanımı oldukça verimlidir.
- `heapq`: Python'da min-heap (öncelikli kuyruk) yapılarını kullanmaya yarayan bir kütüphanedir. `heapq` bu projede, Dijkstra algoritmasının en kısa yolu bulmak için kullanılan öncelikli kuyrukta kullanılmıştır.

## Algoritmaların Çalışma Mantığı
### BFS(Breadth-First Search) Algoritması
Genişlik öncelikli arama algoritmasıdır ve bir grafın tüm düğümleri (istasyonlar) katman katman ziyaret edilerek çözüm bulunur. Bu algoritma şu şekilde çalışır:
1. Başlangıç istasyonu (kök) kuyruğa eklenir.
2. Kuyrukta bulunan her bir istasyon sırayla alınır.
3. İstasyonun komşuları (yani bağlanan diğer istasyonlar) keşfedilir ve kuyruğa eklenir.
4. Bu işlem, hedef istasyon bulunana kadar devam eder.
5. Hedef istasyon bulunduğunda, o ana kadar izlenen yol geri döndürülür.
 **Neden BFS Kullanıyoruz?**
BFS, en kısa yolun her adımda keşfedilmesini sağlar, bu da aktarma sayısını minimize eder. Bu nedenle, "en az aktarmalı" rota bulma problemi için ideal bir algoritmadır.


### A* Algoritması
A* (A-star) algoritması, Dijkstra algoritmasından türetilmiş, ancak bir hedefe daha hızlı ulaşmak için kullanılan bir optimizasyon yapar. A* algoritmasında her düğüm için bir **f** değeri hesaplanır, bu değer şu şekilde hesaplanır:
- **f(n) = g(n) + h(n)**:
  - **g(n)**: Başlangıç noktasından şu ana kadar geçen gerçek maliyet.
  - **h(n)**: Şu anki düğümden hedefe olan tahmin edilen maliyet (heuristic).
A* algoritması, Dijkstra'dan farklı olarak her düğümün maliyetine göre öncelikli sırayla işlem yapar ve hedefe ulaşmak için en uygun rotayı bulur.
 **Neden A* Kullanıyoruz?**
A* algoritması, A* için uygun olan **heuristic** fonksiyonu kullanılarak daha hızlı bir şekilde hedefe ulaşılmasını sağlar. Bu da performans açısından avantajlıdır, çünkü gereksiz düğümleri ve yolları kontrol etmeden doğrudan hedefe yakın olan yolları keşfeder.

## Test Senaryoları
![Test Senaryoları]((https://github.com/niisagulec/MetroSimulation/blob/main/metrosimulation.png))


## Geliştirme Fikirleri
1. Gerçek Zamanlı Veri Entegrasyonu: Metro ağlarındaki güzergahlar ve istasyonlar, gerçek zamanlı trafik ve bakım durumu verilerine dayalı olarak dinamik bir şekilde güncellenebilir. 
2. Gelişmiş Yol Seçenekleri: Kullanıcıların yolculuk tercihlerine göre filtreleme seçenekleri eklenebilir.
3. Kullanıcı Profilleri ve Kişiselleştirme: Kullanıcılar, daha önce kullandıkları rotaları kaydedebilir ve favori istasyonlarını belirleyebilirler.
4. Kullanıcı Dostu Arayüz (GUI): Grafiksel harita ile kullanıcıların metro ağı üzerinde görsel olarak gezinmesini sağlamak için interaktif bir harita arayüzü oluşturulabilir. İstasyonlar ve hatlar harita üzerinde gösterilebilir.
