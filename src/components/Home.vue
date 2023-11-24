<template> 
  <h1 class="d-flex justify-center align-center mt-10">Gerador de QR Codes Hibrit</h1>

  <div class="mt-10">
    <v-row>
      <v-col class="bg-blue">
        <div class="ml-16">
          <qrcode :value="qrData" :size="200"></qrcode>
        </div>
      </v-col>

      <v-col class="bg-blue">
        <h1 class="text-black">Site Agrolito</h1>
        <h1>https://agrolito.com.br/</h1>
        <v-btn class="text-black mt-1" @click="downloadQRCode">Baixar QR Code</v-btn>
      </v-col>
    </v-row>
  </div>

  <div class="mt-10">
    <v-row>
      <v-col class="bg-blue">
        <div class="ml-16">
          <qrcode :value="qrData1" :size="200"></qrcode>
        </div>
      </v-col>

      <v-col class="bg-blue">
        <h1 class="text-black">Site Udemy</h1>
        <h1>https://www.udemy.com/</h1>
        <v-btn class="text-black mt-1" @click="downloadQRCode1">Baixar QR Code</v-btn>
      </v-col>
    </v-row>
  </div>
</template>

<script setup>
import Qrcode from 'vue-qrcode';
import QRCode from 'qrcode';


const components = {
  Qrcode
};

const qrData = 'https://agrolito.com.br/';
const qrData1 = 'https://www.udemy.com/';

const downloadQRCode = async () => {
  try {
    const canvas = await QRCode.toCanvas(qrData);
    const url = canvas.toDataURL('image/png');

    const link = document.createElement('a');
    link.href = url;
    link.download = 'QRCode-Agrolito.png';
    document.body.appendChild(link);
    link.click();
    document.body.removeChild(link);
  } catch (error) {
    console.error('Erro ao gerar o QR Code:', error);
  }
};

const downloadQRCode1 = async () => {
  try {
    const canvas = await QRCode.toCanvas(qrData1);
    const url = canvas.toDataURL('image/png');

    const link = document.createElement('a');
    link.href = url;
    link.download = 'QRCode-Udemy.png';
    document.body.appendChild(link);
    link.click();
    document.body.removeChild(link);
  } catch (error) {
    console.error('Erro ao gerar o QR Code:', error);
  }
};
</script>
