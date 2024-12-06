<script>
export default {
  data() {
    return {
      nama: '',
      usia: null,
      gender: '',
      kelas: 'TI'
    };
  },
  methods: {
    handleSubmit() {
      const siswa = {
        nama: this.nama,
        usia: this.usia,
        gender: this.gender,
        kelas: this.kelas
      };

      this.$emit('tambah-siswa', siswa);
      this.nama = '';
      this.usia = null;
      this.gender = '';
      this.kelas = 'TI';
    }
  }
};
</script>

<template>
  <div>
    <form @submit.prevent="handleSubmit">
      <label for="nama">Nama:</label>
      <input type="text" id="nama" v-model="nama" placeholder="Masukkan nama" /><br /><br />

      <label for="usia">Usia:</label>
      <input type="number" id="usia" v-model="usia" placeholder="Masukkan usia" /><br /><br />

      <label>Gender:</label>
      <label for="laki-laki">
        <input type="radio" id="laki-laki" value="Laki-laki" v-model="gender" /> Laki-laki
      </label>
      <label for="perempuan">
        <input type="radio" id="perempuan" value="Perempuan" v-model="gender" /> Perempuan
      </label><br /><br />

      <label for="kelas">Kelas:</label>
      <select id="kelas" v-model="kelas">
        <option value="TI">TI</option>
        <option value="SI">SI</option>
        <option value="TS">TS</option>
      </select><br /><br />

      <button type="submit">Tambah Siswa</button>
    </form>

    <hr />

    <h2>Data Siswa yang Dimasukkan</h2>
    <div v-if="nama && usia && gender && kelas">
      <p><strong>Nama:</strong> {{ nama }}</p>
      <p><strong>Usia:</strong> {{ usia }}</p>
      <p><strong>Gender:</strong> {{ gender }}</p>
      <p><strong>Kelas:</strong> {{ kelas }}</p>
    </div>
  </div>
</template>

<style scoped>
/* Global Styles */
body {
  font-family: 'Arial', sans-serif;
  margin: 0;
  padding: 0;
  background-color: #f4f4f9;
  color: #333;
}

/* Form Container */
form {
  width: 100%; /* Form memenuhi seluruh layar */
  margin: 0;
  padding: 20px;
  background-color: #ffffff;
  border-radius: 0;
  box-shadow: none;
  box-sizing: border-box;
}

/* Form Elements */
label {
  font-weight: bold;
  margin-bottom: 5px;
  display: block;
  color: #000; /* Warna hitam untuk label */
}

input[type="text"],
input[type="number"],
select {
  width: 100%;
  padding: 10px;
  margin-bottom: 15px;
  border: 1px solid #ccc;
  border-radius: 5px;
  box-sizing: border-box;
}

input[type="radio"] {
  margin-right: 5px;
}

button[type="submit"] {
  background-color: #3498db;
  color: #fff;
  border: none;
  padding: 10px 15px;
  border-radius: 5px;
  font-size: 16px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button[type="submit"]:hover {
  background-color: #2980b9;
}

/* Data Preview Section */
h2 {
  font-size: 1.5rem;
  margin-top: 30px;
  color: #000; /* Warna hitam untuk heading */
}

div {
  width: 100%; /* Latar memenuhi lebar layar */
  margin: 0;
  padding: 20px;
  background: #ffffff;
  border-radius: 0; /* Sudut tidak melengkung */
  box-shadow: none; /* Hilangkan bayangan */
  box-sizing: border-box;
}

p {
  font-size: 1rem;
  margin: 5px 0;
  color: #000; /* Warna hitam untuk teks detail data siswa */
}

/* Responsive Design */
@media screen and (max-width: 768px) {
  form {
    width: 100%; /* Tetap memenuhi lebar layar */
  }

  button[type="submit"] {
    font-size: 14px;
    padding: 8px 12px;
  }

  h2 {
    font-size: 1.3rem;
  }

  p {
    font-size: 0.9rem;
  }
}

@media screen and (max-width: 480px) {
  h2 {
    font-size: 1.1rem;
  }

  p {
    font-size: 0.8rem;
  }
}
</style>
