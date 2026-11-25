# BodyTrackingR15Replicated

BODYTRACKING SYSTEM - INSTALLATION

This system makes players' heads and upper torsos follow their camera
look direction, and replicates that motion so other players see it too.

HOW TO INSTALL (drag each item into the matching service):
   1. PutInReplicatedStorage folder:
      - Move "ProceduralMovement" folder (contains the BodyTracking ModuleScript)
        into ReplicatedStorage.
      - Move the "Events" folder (or just the BodyTrackingAngles
        UnreliableRemoteEvent inside it) into ReplicatedStorage. If you
        already have an "Events" folder there, just move the remote into it.
   2. PutInStarterCharacterScripts folder:
      - Move "BodyTrackingClient" (LocalScript) into
        StarterPlayer > StarterCharacterScripts.
   3. PutInStarterPlayerScripts folder:
      - Move "BodyTrackingReceiver" (LocalScript) into
        StarterPlayer > StarterPlayerScripts.
   4. PutInServerScriptService folder:
      - Move "BodyTrackingRelay" (Script) into ServerScriptService.

 HOW IT WORKS:
   - BodyTrackingClient samples the local camera's yaw/pitch at 12 Hz and
     sends it to the server via the BodyTrackingAngles UnreliableRemoteEvent.
   - BodyTrackingRelay (server) validates and rate-limits the data, then
     broadcasts it to the other clients.
   - BodyTrackingReceiver (on other clients) applies the angles to that
     player's character using the BodyTracking module (Waist/Neck Motor6D).

 OPTIONAL CHARACTER ATTRIBUTES (set on the character Model):
   - RiderFacingBlend (number, 0-1): blends in a rider-facing pose
   - RiderFacingOffset (number): yaw offset for the rider pose
   - Ragdolled (bool): suspends joint writes while true

 NOTE: Designed for R15 characters (uses UpperTorso/Head Motor6D joints).

 INDONESIAN:

 Sistem ini membuat kepala dan uppertorso pemain mengikuti arah pandangan
 kamera player, dan juga sistem ini sudah mereplikasi pergerakan tubuh player ke server agar bisa di lihat oleh player lain.
 (Clinet > Server > Client)

 CARA PEMASANGAN (pindahkan setiap item ke layanan/service yang sesuai):
   1. Folder PutInReplicatedStorage:
      - Pindahkan folder "ProceduralMovement" (ModuleScript BodyTracking)
        ke dalam ReplicatedStorage.
      - Pindahkan folder "Events" (atau cukup pindahkan UnreliableRemoteEvent
        "BodyTrackingAngles") ke dalam ReplicatedStorage. Jika
        sudah ada folder "Events" di sana, pindahkan saja remote tersebut ke dalamnya.
   2. Folder PutInStarterCharacterScripts:
      - Pindahkan "BodyTrackingClient" (LocalScript) ke dalam
        StarterPlayer > StarterCharacterScripts.
   3. Folder PutInStarterPlayerScripts:
      - Pindahkan "BodyTrackingReceiver" (LocalScript) ke dalam
        StarterPlayer > StarterPlayerScripts.
   4. Folder PutInServerScriptService:
      - Pindahkan "BodyTrackingRelay" (Script) ke dalam ServerScriptService.

 CARA KERJA:
   - BodyTrackingClient mengambil sampel yaw/pitch kamera lokal pada frekuensi 12 Hz dan
     mengirimkannya ke server melalui UnreliableRemoteEvent "BodyTrackingAngles".
   - BodyTrackingRelay (di sisi server) memvalidasi dan membatasi laju (rate-limit) data tersebut,
     kemudian menyebarkannya ke klien lain.
   - BodyTrackingReceiver (di klien lain) menerapkan sudut-sudut tersebut pada karakter
     pemain terkait menggunakan modul BodyTracking (melalui Motor6D pada bagian Pinggang/Leher).

 ATRIBUT KARAKTER OPSIONAL (diatur pada Model karakter):
   - RiderFacingBlend (angka, 0-1): mencampur pose menghadap ke depan (seperti posisi pengendara)
   - RiderFacingOffset (angka): offset yaw untuk pose pengendara tersebut
   - Ragdolled (boolean): menghentikan pembaruan sendi (joint) saat bernilai true

 CATATAN: Dirancang untuk karakter tipe R15 (menggunakan sendi Motor6D pada UpperTorso/Head).
 Tambahan: kamu bisa tweak smoothess, angle dan lain lainnya di dalam modul BodyTracking.
 dah gitu aja wkwkw!!
