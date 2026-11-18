# Rastgele keşif — yalnız araştırma

Bu özellik bu değişiklik setinde uygulanmaz. Önce uygulama UI'sında davranış belirlenip sonra aynı özelliğe MCP tetikleyicisi eklenmesi önerilir. AI parça seçmez; platform havuzları ve yerel RNG kullanılır.

## Yakın
Beğenilenler veya recentHistory içinden rastgele seed seçilip YtMusicRepository.radio(seed) kullanılır. Seed, tekrarlar ve yakın zamanda çalınanlar elenir. Platform benzerliği garanti edilmez; güçlü kişisel kaynak bağlantısı sağlanır.

## Orta
quickPicks/home/mixedForYou ve tür/ruh hali havuzları karıştırılır. Örneğin %30 kişisel/%70 keşif bir ürün politikasıdır; ölçülmüş müzikal uzaklık değildir. Mix kartlarının parçaları ayrıca çözülür. Son filtre, fallback'in eski parçaları yeniden getirmesini engeller.

## Uzak
Tür → playlist → parça havuzlarında yerel RNG kullanılabilir. Tüm katalogdan uniform random API/enkvanteri incelenen kodda yoktur. Eşit olasılık yalnız toplanan tekilleştirilmiş havuz için mümkündür; kategori, bölge, playlist boyutu ve platform sıralaması yanlılık üretir.
Mevcut mood/browse çağrıları oturum kullanır. Gerçek hesap-bağımsız keşif için ayrı anonymous browse ve continuation context gerekir; global auth geçici kapatılmamalı. Anonymous search bile dil/bölge/visitorData etkilerini taşıyabilir. searchContinuation normal oturum yoluna dönebilir.

## Maliyet
Önbellek önce; yenilemede başlangıç bütçesi 3–5 mantıksal istek, sınırlı sayfalama. Her tıklamada tüm beğenileri sync etme veya parça başına metadata sorgulama yok. Pil etkisi ölçülmemiştir.

## Kaynaklar
shared/src/jvmSharedMain/kotlin/com/music/bitchord/data/YtMusicRepository.kt: radio, quickPicks, moodAndGenres, moodGenreShelves, mixedForYou, recentHistory, searchPage, searchContinuation.
shared/src/jvmSharedMain/kotlin/com/music/bitchord/data/innertube/Innertube.kt: anonymous search ve oturum bağlamı.
Araştırma kaynak kodu düzeyindedir; gerçek hesap API testi ve UI implementasyonu yapılmamıştır.
