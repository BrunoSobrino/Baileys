[![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/colored.png)](#table-of-contents)
# Baileys Up To Date

 ------
 Arreglos y/o correcciones - Fixes and/or corrections - Perbaikan dan/atau koreksi:
 
 - Baileys con Botones arreglados excepto los botones de templateButtons, además los mensajes de lista solo están disponibles en chats privados. Igual se corrigieron mensajes de error en la consola (solo visual).
 
 - Baileys with Buttons fixed except for templateButtons, also list messages are only available in private chats. Also fixed error messages in the console (visual only).
 
 - Baileys dengan Buttons diperbaiki kecuali templateButtons, plus pesan daftar hanya tersedia di obrolan pribadi. Pesan kesalahan yang sama diperbaiki di konsol (hanya visual).
 ------
 Puntos importantes a considerar - Important points to consider - Poin penting untuk dipertimbangkan:
 
 - La conexión debe ser con un WhatsApp normal no Business para que los botones sean enviados.
 
 - The connection must be with a normal WhatsApp not Business for the buttons to be sent
 
 - Koneksi harus dengan WhatsApp biasa, bukan Bisnis agar tombol dapat dikirim
 ------

 > **Warning**: Esto es solo un repositorio de Baileys que ha sido actualizado y arreglado si hay problemas. Hace mas facil para los principiantes si hay un pull request en el repositorio principal que no ha sido acreditado.
 
 > **Note**: Si hay problemas o cuestiones, pregunte al grupo siguiente
 
GRUP INFO BAILEYS: [KLIK DISINI](https://chat.whatsapp.com/Htfi5uzYWOt0ekPu66YK4Y)

#### Las actualizaciones están temporalmente suspendidas, actualmente se están actualizando otras bibliotecas y la nueva base en este repositorio.

### Lea toda la información a continuación para saber

## 🔥 ConnectionOptions
> **Note**: Ajustes adicionales de la opción de la conexión como abajo primero
```
const connectionOptions = {
printQRInTerminal: true, // mostrar qr en el terminal
syncFullHistory: false, // recibir un historial completo
markOnlineOnConnect: false, // marcar el Bot como siempre en linea
connectTimeoutMs: 60_000, // establecer el tiempo de espera
defaultQueryTimeoutMs: 0, // establecer el periodo de tiempo de consulta (0: sin límite)
keepAliveIntervalMs: 10000, // interval ws
generateHighQualityLinkPreview: true, // aumentar la calidad de las vistas previas en miniatura
// parche de botones: no funcional actualmente
patchMessageBeforeSending: (message) => {
    const requiresPatch = !!(
        message.buttonsMessage 
        || message.templateMessage
        || message.listMessage
    );
    if (requiresPatch) {
        message = {
            viewOnceMessage: {
                message: {
                    messageContextInfo: {
                        deviceListMetadataVersion: 2,
                        deviceListMetadata: {},
                    },
                    ...message,
                },
            },
        };
    }

    return message;
},
getMessage: async (key) => {
         if (store) {
            const msg = await store.loadMessage(key.remoteJid, key.id)
            return msg.message || undefined
         }
         return {
            conversation: "hello, i'm BrunoSobrino"
         }
      },
// obtener el mensaje anterior para resolver el mensaje no se pudo enviar, "en espera de mensaje", se puede intentar de nuevo
}
```
