<template>
  <v-row>
    <v-col class="bg-black d-flex justify-center align-center">
      <div>
        <qrcode class="mt-10 mb-10" :value="qrData" :size="200"></qrcode>
      </div>
      <div class="ml-5">
        <v-btn class="text-black" @click="downloadQRCode">Baixar QR Code</v-btn>
      </div>
    </v-col>

    <v-col class="bg-black">
      <h1>Site Agrolito</h1>
      <h2 class="mt-5">https://agrolito.com.br/</h2>
    </v-col>
  </v-row>
</template>

<script setup>
import Qrcode from 'vue-qrcode';
import QRCode from 'qrcode';


const components = {
  Qrcode
};

const qrData = 'https://agrolito.com.br/';

const downloadQRCode = async () => {
  try {
    const canvas = await QRCode.toCanvas(qrData);
    const url = canvas.toDataURL('image/png');

    const link = document.createElement('a');
    link.href = url;
    link.download = 'qrcode.png';
    document.body.appendChild(link);
    link.click();
    document.body.removeChild(link);
  } catch (error) {
    console.error('Erro ao gerar o QR Code:', error);
  }
};
</script>
