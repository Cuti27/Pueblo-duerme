<template>
    <FlexboxLayout flexDirection="column" justifyContent="center"
        alignItems="center">
        <Label textWrap="true" text="Añade nuevos jugadores"
            class="h2 description-label"></Label>
            
        <TextField v-model="playerName" hint="Nombre del jugador"></TextField>
        <Button @tap="AddPlayer">Agregar</Button>
    </FlexboxLayout>
</template>

<script>
    export default {
        data() {
            return {
                playerName: ""
            };
        },
        methods: {
            AddPlayer() {
                if (this.playerName != "") {
                    this.$emit("add", this.playerName);
                    this.playerName = "";
                }
            }
        }
    };
</script>

<style scoped>
</style>