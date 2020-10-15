<template>
    <div>
        <h1>Roles</h1>
        <ul v-if="rol.items">
            <li v-for="rol in rol.items" :key="rol.rolId">
                {{rol.descripcion}}
                <span v-if="rol.deleting"><em> - Deleting...</em></span>
                <span v-else-if="rol.deleteError" class="text-danger"> - ERROR: {{rol.deleteError}}</span>
                <span v-else> - <a @click="delete(rol.rolId)" class="text-danger">Delete</a></span>
            </li>
        </ul>
        
    </div>
</template>

<script>
import { rolService } from '../_services'
export default {
     data () {
        return {
            rol: {
                descripcion: '',
            },
        }
    },
    created () {
        this.getAllRoles();
    },
    methods: {
        getAllRoles(){
            var data = rolService.getAll();
            console.log(data);
        }
    }
}
</script>