<template>
  <h1 class="d-flex justify-center align-center mt-10">Gerador de QR Codes Hibrit</h1>

  <div class="mt-10">
    <v-row>
      <v-col class="bg-blue" md="3">
        <div class="ml-16 pl-16">
          <qrcode :value="qrData" :size="200" height="180"></qrcode>
        </div>
      </v-col>

      <v-col class="bg-blue pr-16" md="3">
        <h1 class="text-black">Agrolito | Site</h1>
        <h3>https://agrolito.com.br/</h3>
        <v-btn class="text-black mt-2" @click="downloadQRCode">Baixar QR Code</v-btn>
      </v-col>
    </v-row>
  </div>

  <div class="mt-10">
    <v-row>
      <v-col class="bg-blue">
        <div class="ml-16 pl-16">
          <qrcode :value="qrData1" :size="200"></qrcode>
        </div>
      </v-col>
      
      <v-col class="bg-blue pr-16">
        <h1 class="text-black">Agrolito | Cartão de Visitas</h1>
        <h3>https://agrolito.com.br/?utm_campaign=qr-hibrit&utm_source=cartao&utm_medium=qrcode</h3>
        <v-btn class="text-black mt-2" @click="downloadQRCode1">Baixar QR Code</v-btn>
      </v-col>
    </v-row>
  </div>

  <div class="mt-10">
    <v-row>
      <v-col class="bg-blue">
        <div class="ml-16 pl-16">
          <qrcode :value="qrData1" :size="200"></qrcode>
        </div>
      </v-col>
      
      <v-col class="bg-blue pr-16">
        <h1 class="text-black">Agrolito | Saco 25Kg</h1>
        <h3>https://agrolito.com.br/?utm_campaign=qr-hibrit&utm_source=saco-25kg&utm_medium=qrcode</h3>
        <v-btn class="text-black mt-2" @click="downloadQRCode2">Baixar QR Code</v-btn>
      </v-col>
    </v-row>
  </div>

  <div class="mt-10">
    <v-row>
      <v-col class="bg-blue">
        <div class="ml-16 pl-16">
          <qrcode :value="qrData1" :size="200"></qrcode>
        </div>
      </v-col>
      
      <v-col class="bg-blue pr-16">
        <h1 class="text-black">Agrolito | Ficha Técnica</h1>
        <h3>https://agrolito.com.br/?utm_campaign=qr-hibrit&utm_source=ficha-tecnica&utm_medium=qrcode</h3>
        <v-btn class="text-black mt-2" @click="downloadQRCode3">Baixar QR Code</v-btn>
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
const qrData1 = 'https://agrolito.com.br/?utm_campaign=qr-hibrit&utm_source=cartao&utm_medium=qrcode';
const qrData2 = 'https://agrolito.com.br/?utm_campaign=qr-hibrit&utm_source=saco-25kg&utm_medium=qrcode';
const qrData3 = 'https://agrolito.com.br/?utm_campaign=qr-hibrit&utm_source=ficha-tecnica&utm_medium=qrcode';


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
    link.download = 'QRCode-Agrolito-Cartão-de-visitas.png';
    document.body.appendChild(link);
    link.click();
    document.body.removeChild(link);
  } catch (error) {
    console.error('Erro ao gerar o QR Code:', error);
  }
};

const downloadQRCode2 = async () => {
  try {
    const canvas = await QRCode.toCanvas(qrData2);
    const url = canvas.toDataURL('image/png');

    const link = document.createElement('a');
    link.href = url;
    link.download = 'QRCode-Agrolito-Saco-25kg.png';
    document.body.appendChild(link);
    link.click();
    document.body.removeChild(link);
  } catch (error) {
    console.error('Erro ao gerar o QR Code:', error);
  }
};

const downloadQRCode3 = async () => {
  try {
    const canvas = await QRCode.toCanvas(qrData3);
    const url = canvas.toDataURL('image/png');

    const link = document.createElement('a');
    link.href = url;
    link.download = 'QRCode-Agrolito-Ficha-Tecnica.png';
    document.body.appendChild(link);
    link.click();
    document.body.removeChild(link);
  } catch (error) {
    console.error('Erro ao gerar o QR Code:', error);
  }
};
</script>
