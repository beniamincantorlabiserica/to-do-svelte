<script>
	import HeroText from "../lib/components/HeroText.svelte";
	import Footer from "../lib/components/Footer.svelte";
	import DottedCallOut from "../lib/components/DottedCallOut.svelte";
	import Todo from "../lib/components/Todo.svelte"
	import ReadMe from "../lib/components/ReadMe.svelte"
	import { onMount } from "svelte";
	import toast, { Toaster } from 'svelte-french-toast';
	import Faq from "../lib/components/FAQ.svelte";


    onMount(() => {
		toast.success("It works!");
	})

    function seetoast() {
        toast.error('something went wrong')
    }
</script>

<HeroText />

<Todo />
<Toaster />
<ReadMe />
<Footer />
