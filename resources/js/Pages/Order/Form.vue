<template>
    <div class="p-6 h-full">

        <Body>
            <div class="grid grid-cols-2 gap-4">
                <div>
                    <div class="pl-6 pb-6">
                        <label class="floating-label">
                            <input type="text" placeholder="Nome do Resposável" class="input input-md text-white w-full"
                                 name="responsible" id="responsible" />
                            <span class="text-white">Nome do Resposável</span>
                        </label>
                    </div>
                    <div class="pl-6 pb-6">
                        <label class="floating-label">
                            <input type="text" class="input input-md text-white w-full" 
                                placeholder="Nome do cliente" name="client" id="client" />
                            <span class="text-white">Nome do cliente</span>
                        </label>
                    </div>
                    <div class="pl-6 pb-6">
                        <label class="floating-label" popovertarget="cally-popover1">
                            <input type="text" class="input input-md text-white w-full pika-single" placeholder="Data do Pedido"
                                 name="date_order" id="date_order" ref="date_order"/>
                            <span class="text-white">Data pedido</span>
                        </label>
                    </div>
                    <div class="pl-6 pb-6">
                        <label class="floating-label">
                            <input type="text" class="input input-md text-white w-full" placeholder="Data da Entrega"
                                 name="date_delivered" id="date_delivered" ref="date_delivered"/>
                            <span class="text-white">Data entregue</span>
                        </label>
                    </div>
                    <div class="pl-6 pb-6">
                        <label class="floating-label">
                            <input type="text" class="input input-md text-white w-full" placeholder="Data do Vencimento"
                                 name="date_due" id="date_due" ref="date_due"/>
                            <span class="text-white">Data vencimento</span>
                        </label>
                    </div>
                    <div class="h-full flex ">
                        <button class="btn btn-success">Salvar</button>
                    </div>
                </div>
                <div>
                    <div class="pl-6 pb-3">
                        <ButtonAdd :action="openModalMedicine" />
                        <dialog id="modalMedicamentos" class="modal">
                            <div class="modal-box w-11/12 max-w-5xl">
                                <h3 class="text-lg font-bold">Medicamento</h3>
                                <div class="pl-6 pt-6">
                                    <label class="floating-label">
                                        <input type="file" class="file-input" />
                                        <span class="text-white">Imagem</span>
                                    </label>
                                </div>
                                <div class="pl-6 pt-6">
                                    <label class="floating-label">
                                        <input type="text" class="input input-md text-white w-full"
                                            placeholder="Nome" name="name" id="name" />
                                        <span class="text-white">Nome</span>
                                    </label>
                                </div>
                                <div class="pl-6 pt-6">
                                    <label class="floating-label">
                                        <input type="text" class="input input-md text-white w-full"
                                            placeholder="Valor" name="price" id="price" @input="formatPrice"/>
                                        <span class="text-white">Valor</span>
                                    </label>
                                </div>
                                <div class="pl-6 pt-6">
                                    <label class="floating-label">
                                        <input type="text" class="input input-md text-white w-full" placeholder="Data do Vencimento"
                                         name="date_due" id="date_due" ref="date_due"/>
                                        <span class="text-white">Data vencimento</span>
                                    </label>
                                </div>
                                <div class="pl-6 pt-6">
                                    <label class="floating-label">
                                        <input type="number" class="input input-md text-white w-full"
                                            placeholder="Dosagem" name="dosage" id="dosage" />
                                        <span class="text-white">Dosagem</span>
                                    </label>
                                </div>
                                <div class="modal-action">
                                    <form method="dialog" >
                                        <div class="flex justify-end pt-6 w-full gap-5">
                                            <!-- if there is a button, it will close the modal -->
                                            <button class="btn btn-error">Fechar</button>
                                            <button class="btn btn-primary">Adicionar</button>

                                        </div>
                                    </form>
                                </div>
                            </div>
                        </dialog>
                        
                    </div>
                    <div class="overflow-x-auto">
                        <table class="table bg-black shadow-md rounded-lg">
                            <!-- head -->
                            <thead>
                                <tr>
                                    <th>
                                        <label>
                                            <input type="checkbox" class="checkbox" />
                                        </label>
                                    </th>
                                    <th>Imagem</th>
                                    <th>Nome</th>
                                    <th>Valor</th>
                                    <th>Vencimento</th>
                                    <th>Dosagem</th>
                                    <th></th>
                                </tr>
                            </thead>
                            <tbody>
                                <!-- row 1 -->
                                <tr>
                                    <th>
                                        <label>
                                            <input type="checkbox" class="checkbox" />
                                        </label>
                                    </th>
                                    <td>
                                        <div class="flex items-center gap-3">
                                            <div class="avatar">
                                                <div class="mask mask-squircle h-12 w-12">
                                                    <img src="https://img.daisyui.com/images/profile/demo/2@94.webp"
                                                        alt="Avatar Tailwind CSS Component" />
                                                </div>
                                            </div>
                                            <div>
                                                <div class="font-bold">Hart Hagerty</div>
                                                <div class="text-sm opacity-50">United States</div>
                                            </div>
                                        </div>
                                    </td>
                                    <td>
                                        Zemlak, Daniel and Leannon
                                        <br />
                                        <span class="badge badge-ghost badge-sm">Desktop Support Technician</span>
                                    </td>
                                    <td>Purple</td>
                                    <th>
                                        <button class="btn btn-ghost btn-xs">details</button>
                                    </th>
                                </tr>
                                <!-- row 2 -->
                                <tr>
                                    <th>
                                        <label>
                                            <input type="checkbox" class="checkbox" />
                                        </label>
                                    </th>
                                    <td>
                                        <div class="flex items-center gap-3">
                                            <div class="avatar">
                                                <div class="mask mask-squircle h-12 w-12">
                                                    <img src="https://img.daisyui.com/images/profile/demo/3@94.webp"
                                                        alt="Avatar Tailwind CSS Component" />
                                                </div>
                                            </div>
                                            <div>
                                                <div class="font-bold">Brice Swyre</div>
                                                <div class="text-sm opacity-50">China</div>
                                            </div>
                                        </div>
                                    </td>
                                    <td>
                                        Carroll Group
                                        <br />
                                        <span class="badge badge-ghost badge-sm">Tax Accountant</span>
                                    </td>
                                    <td>Red</td>
                                    <th>
                                        <button class="btn btn-ghost btn-xs">details</button>
                                    </th>
                                </tr>
                                <!-- row 3 -->
                                <tr>
                                    <th>
                                        <label>
                                            <input type="checkbox" class="checkbox" />
                                        </label>
                                    </th>
                                    <td>
                                        <div class="flex items-center gap-3">
                                            <div class="avatar">
                                                <div class="mask mask-squircle h-12 w-12">
                                                    <img src="https://img.daisyui.com/images/profile/demo/4@94.webp"
                                                        alt="Avatar Tailwind CSS Component" />
                                                </div>
                                            </div>
                                            <div>
                                                <div class="font-bold">Marjy Ferencz</div>
                                                <div class="text-sm opacity-50">Russia</div>
                                            </div>
                                        </div>
                                    </td>
                                    <td>
                                        Rowe-Schoen
                                        <br />
                                        <span class="badge badge-ghost badge-sm">Office Assistant I</span>
                                    </td>
                                    <td>Crimson</td>
                                    <th>
                                        <button class="btn btn-ghost btn-xs">details</button>
                                    </th>
                                </tr>
                                <!-- row 4 -->
                                <tr>
                                    <th>
                                        <label>
                                            <input type="checkbox" class="checkbox" />
                                        </label>
                                    </th>
                                    <td>
                                        <div class="flex items-center gap-3">
                                            <div class="avatar">
                                                <div class="mask mask-squircle h-12 w-12">
                                                    <img src="https://img.daisyui.com/images/profile/demo/5@94.webp"
                                                        alt="Avatar Tailwind CSS Component" />
                                                </div>
                                            </div>
                                            <div>
                                                <div class="font-bold">Yancy Tear</div>
                                                <div class="text-sm opacity-50">Brazil</div>
                                            </div>
                                        </div>
                                    </td>
                                    <td>
                                        Wyman-Ledner
                                        <br />
                                        <span class="badge badge-ghost badge-sm">Community Outreach Specialist</span>
                                    </td>
                                    <td>Indigo</td>
                                    <th>
                                        <button class="btn btn-ghost btn-xs">details</button>
                                    </th>
                                </tr>
                            </tbody>
                            <!-- foot -->
                            <tfoot>
                                <tr>
                                    <th></th>
                                    <th>Imagem</th>
                                    <th>Nome</th>
                                    <th>Job</th>
                                    <th>Vencimento</th>
                                    <th>Dosagem</th>
                                    <th></th>
                                </tr>
                            </tfoot>
                        </table>
                    </div>
                </div>
            </div>
        </Body>

    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import Body from '@/Components/Body.vue';
import ButtonAdd from '@/Components/ButtonAdd.vue';
import Pikaday from "pikaday";
import moment from "moment";

// Refs para os campos de data
const date_order = ref(null);
const date_delivered = ref(null);
const date_due = ref(null);
const price = ref("");

// Função para inicializar os Datepickers
const initDatepickers = () => {
    new Pikaday({
        format: 'DD/MM/YYYY',
        field: date_order.value ? date_order.value : null,
        toString(date, format) {
            return moment(date).format(format);
        },
        parse(dateString, format) {
            return moment(dateString, format).toDate();
        }
    });

    new Pikaday({
        format: 'DD/MM/YYYY',
        field: date_delivered.value ? date_delivered.value : null,
        toString(date, format) {
            return moment(date).format(format);
        },
        parse(dateString, format) {
            return moment(dateString, format).toDate();
        }
    });

    new Pikaday({
        format: 'DD/MM/YYYY',
        field: date_due.value ? date_due.value : null,
        toString(date, format) {
            return moment(date).format(format);
        },
        parse(dateString, format) {
            return moment(dateString, format).toDate();
        }
    });
};

// Inicializa os datepickers ao montar o componente
onMounted(() => {
    initDatepickers();
});

// Função para abrir o modal
const openModalMedicine = () => {
    const modal = document.getElementById('modalMedicamentos');
    modal.showModal();
};

// Função para formatar o preço
const formatPrice = () => {
    let num = parseFloat(price.value.replace(/\D/g, '')) / 100 || 0;
    price.value = num.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL' });
};
</script>

<style lang="scss" scoped></style>