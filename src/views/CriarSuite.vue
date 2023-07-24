<template>
    <div>
        <b-form @submit.prevent="cadastrarSuite">
            <b-form-group label="Nome da Suite:" label-for="nomeSuite">
                <b-form-input v-model="nomeSuite" id="nomeSuite" type="text" size="sm" placeholder="Digite o nome da suite"
                    required></b-form-input>
            </b-form-group>

            <b-button type="submit" variant="primary">Cadastrar</b-button>
        </b-form>
    </div>
</template>
  
<script>
import Swal from 'sweetalert2';

export default {
    data() {
        return {
            nomeSuite: "",
            url: "http://192.168.0.17:3001/suites",
        };
    },
    methods: {
        async cadastrarSuite() {
            const data = {
                nomeSuite: this.nomeSuite,
            };

            try {
                console.log(JSON.stringify(data));
                const response = await fetch(this.url, {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                    },
                    body: JSON.stringify(data),
                });

                const responseData = await response.json()
                console.log(responseData);
                if (response.status == 201) {
                    this.nomeSuite = '';
                    Swal.fire('Suite cadastrada com sucesso!', `Id da suite: ${responseData.id_suite}`, 'success')
                } else {
                    Swal.fire('Erro ao cadastrar suite!', responseData.error, 'error');
                }
            } catch (error) {
                console.error(error);

            }
        },
    },
};
</script>
  