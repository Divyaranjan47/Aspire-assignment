<template>
    <article class="accrodion-container">
        <Accordion :open="false">
            <template v-slot:acc-head>
                <img class="img" src="../assets/card-acc.svg" alt="" />
                <span class="text">Card details</span>
            </template>
            <template v-slot:acc-content>
                i am content
            </template>
        </Accordion>
        <Accordion :open="true">
            <template v-slot:acc-head>
                <img class="img" src="../assets/trans-acc.svg" alt="" />
                <span class="text">Recent transactions</span>
            </template>
            <template v-slot:acc-content>
                <ExpenseBar v-for="tran in trans" :key="tran.id" :transaction="tran" />
            </template>
            <template v-slot:acc-add>
                <DetailsAction :text="'View all card transactions'" />
            </template>
        </Accordion>
    </article>
</template>

<script>
import Accordion from './common/Accordion';
import ExpenseBar from './common/ExpenseBar';
import DetailsAction from './common/DetailsAction';
// constamt import for data
import transactionDetails from '../constants/transaction-details.js';

export default {
    name: 'AccordionContainer',
    components: {
        Accordion,
        ExpenseBar,
        DetailsAction
    },
    data() {
        return {
            trans: transactionDetails.transactions
        }
    }
}
</script>

<style>

</style>