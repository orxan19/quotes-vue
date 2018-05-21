<template>
    <div class="container">
		<app-header :quote-count="quotes.length" v-bind:max-quotes="maxQuotes"></app-header>
		<app-new-quote @quoteAdded="newQuote"></app-new-quote>
    	<app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
    	<div class="row">
    		<div class="col-sm-12 text-center">
    			<div class="alert alert-info">Info: Click to delete</div>
    		</div>
    	</div>
    </div>
</template>

<script>
	import QuoteGrid from './components/QuoteGrid.vue';
	import NewQuote from './components/NewQuote.vue';
	import Header from './components/Header.vue';

    export default {
        data: function(){
        	return {
        		quotes: [
        			'Just a Quote by default',
        			'For test example'
        		],
        		maxQuotes: 10

        	}
        },
        methods: {
            newQuote: function (quote) {

                if (this.quotes.length < this.maxQuotes) {
                    if (quote != "" && quote != " ") {
                        this.quotes.push(quote);
                    } else {
						alert('Do not input empty string');

                    }

                } else {
                    alert('Max number of quotes is 10');
                }
            },
            deleteQuote: function (index) {
                this.quotes.splice(index, 1);
            }
        },
        components: {
        	appQuoteGrid: QuoteGrid,
        	appNewQuote: NewQuote,
			appHeader: Header
        }
    }
</script>

<style>
</style>
