!pip install qrcode[pil] --quiet   # Instala a biblioteca (só precisa rodar uma vez)

import qrcode
from qrcode.image.styledpil import StyledPilImage
from qrcode.image.styles.moduledrawers import RoundedModuleDrawer
from PIL import Image

# === CONTEÚDO DO QR CODE ===
conteudo = """[Português]
Pindamonhangaba (SP) - Brasil
Rua Dr. Martiniano Salgado
Início: Nº 13 | Final: Nº 74
Loteamento São Judas Tadeu
Bairro Alvarengas

[English]
Pindamonhangaba (SP) - Brazil
Dr. Martiniano Salgado Street
Start: No. 13 | End: No. 74
São Judas Tadeu Subdivision
Alvarengas Neighborhood

[Español]
Pindamonhangaba (SP) - Brasil
Calle Dr. Martiniano Salgado
Inicio: Nº 13 | Fin: Nº 74
Subdivisión São Judas Tadeu
Barrio Alvarengas

🔗 Google Maps: https://maps.google.com/?q=Rua+Dr.+Martiniano+Salgado,+Pindamonhangaba
"""

# Cria o QR Code
qr = qrcode.QRCode(
    version=1,
    error_correction=qrcode.constants.ERROR_CORRECT_H,
    box_size=10,
    border=4,
)

qr.add_data(conteudo)
qr.make(fit=True)

# Gera a imagem
img = qr.make_image(
    fill_color="black",
    back_color="white",
    image_factory=StyledPilImage,
    module_drawer=RoundedModuleDrawer()
)

# Salva o arquivo
img.save("QR_Code_Multilingue_Ana_Lucia.png")
print("✅ QR Code gerado com sucesso!")

# Mostra o QR Code dentro do Colab
img
