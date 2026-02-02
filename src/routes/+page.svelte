<script>
	import { onMount } from 'svelte';

	// Product data
	const products = [
		{
			id: 1,
			name: 'Nike Air Max Red',
			description: 'Performance Redefined',
			price: 120.00,
			image: 'https://lh3.googleusercontent.com/aida-public/AB6AXuCqA_6cyZXKBhp1gT1VWD6WXJnikofIErYycstxgtUdYBL8wAnJwr6MoIwCiYryQEo3GBRUlG1_7cuJiUOFL0gAiAUhzzsY1-dx19KwS7_YS6CH62-Mau2TuHHG1_x7G_Swrf-gDIVSpGzy4mkNFnPJfJ8pawoeeXp7p1fyZOvLXTk9VrtwIom9y3rmld3sWdUqymh2eDpGjrJbYInTUfPy8fYEa_Qo-6g-2fVtL98D0UKVLTnqK7pF7NJy_SN3jLKHv-oFeQVXP6E8',
			liked: true
		},
		{
			id: 2,
			name: 'Aesthetic Watch S',
			description: 'Modern Minimalist',
			price: 89.00,
			image: 'https://lh3.googleusercontent.com/aida-public/AB6AXuBy8Ohvj5e7g89vSQLSvV_JlXqFEaQR39bY4kj5eGb_UNe-A45KtKCIEzBVlcxmrrYKnvnXpoVi4oZLWC0-dUWg2BPWFjyAVYed9hsh_rabFZT4R7xZMgMtFseO9wTwzdJ1wlqob7W5CjjdCv7P8qnHTNdiWu2996wS5iu_GxQxriOjlwNQhlVdyJJmh_rDKjuXdQEDKn3IcBNkodPYQi2UF8YYo2ryIbhFeJvxB_COyBpBetxpZ2Isj6iqCHAOTkq9tsWlr9X4r9SW',
			liked: false
		},
		{
			id: 3,
			name: 'Studio Wireless Pro',
			description: 'Immersive Audio',
			price: 249.00,
			image: 'https://lh3.googleusercontent.com/aida-public/AB6AXuADLd3u-_H6AkKSEtvl6vYPke6Wmls-UQz0MEX9b4emgYi2F8Vm_H2VqJ5x2uyy6bS04LAsFmjJYiUDXUW1jtsw-S83emc8XZl_wd3mOkBgIdCcxxWdRLXVqZ5M2JRubY7YUQipNfskuLY9Zc9opBWRacOhsoU2R-Mk4A0W4VmcUVNytf2htmHNjoac1_SYGFy19NG8NcNuT3KFJ4BkkiumgvACXTf3ZceQCLBwKXhmQaeE7ZUgTyImbqnN37xuDW-O7EkehEzZExKQ',
			liked: false
		},
		{
			id: 4,
			name: 'Classic Shades',
			description: 'UV400 Protection',
			price: 45.00,
			image: 'https://lh3.googleusercontent.com/aida-public/AB6AXuAC01Yp1cB9_z9Kj20M6U45x2LsdUog74RlfFt1Ut9S8ADrR8M8pFwIVWb7j4hNllgNU3xONbKpnhO2BsjpQoiZJcw-Aezx_gzgsgeMpoBJA_3ud9U3TLP0ojwoch9zIjPPwc8CKxnG5C_72HTUUFhgcUvGweJYA-9EI-ohi-hJwIIzVeRFz9sVUW3jzGQv7hpFMPGiyQfU3gbxPZQ6OWbkRiIQ-h-29m3c7wqjaeUNwgx9gd9NVGxzR-5zoWe1GJY15yVMtvecZZxq',
			liked: false
		}
	];

	const categories = ['All', 'Sneakers', 'Watches', 'Jackets', 'Gadgets'];
	let activeCategory = 'All';
	let isDarkMode = false;

	// Dark mode toggle function
	function toggleDarkMode() {
		isDarkMode = !isDarkMode;
		if (typeof document !== 'undefined') {
			document.documentElement.classList.toggle('dark', isDarkMode);
			localStorage.setItem('darkMode', isDarkMode ? 'dark' : 'light');
		}
	}

	// Initialize dark mode from localStorage
	onMount(() => {
		const savedMode = localStorage.getItem('darkMode');
		isDarkMode = savedMode === 'dark';
		document.documentElement.classList.toggle('dark', isDarkMode);
	});
</script>

<!-- Header -->
<header class="sticky top-0 z-40 px-6 pt-12 pb-4 bg-background-light/80 dark:bg-background-dark/80 ios-blur">
	<div class="flex items-center justify-between mb-6">
		<div>
			<p class="text-sm font-medium text-slate-500 dark:text-slate-400">Discover</p>
			<h1 class="text-3xl font-extrabold tracking-tight">
				<span class="dark:text-white">New</span> <span class="text-gradient">Collection</span>
			</h1>
		</div>
		<div class="flex items-center gap-2">
			<button 
				on:click={toggleDarkMode}
				class="w-10 h-10 flex items-center justify-center rounded-full bg-slate-100 dark:bg-slate-800 transition-colors"
				aria-label="Toggle dark mode"
			>
				<span class="material-icons-round text-xl">
					{isDarkMode ? 'light_mode' : 'dark_mode'}
				</span>
			</button>
			<button class="w-10 h-10 flex items-center justify-center rounded-full bg-slate-100 dark:bg-slate-800">
				<span class="material-icons-round text-xl">notifications_none</span>
			</button>
		</div>
	</div>
	<div class="relative">
		<span class="material-icons-round absolute left-4 top-1/2 -translate-y-1/2 text-slate-400">search</span>
		<input 
			class="w-full pl-12 pr-4 py-4 rounded-2xl bg-white dark:bg-slate-800 border-none soft-shadow focus:ring-2 focus:ring-primary/20 dark:placeholder:text-slate-500" 
			placeholder="Search products..." 
			type="text"
		/>
	</div>
</header>

<!-- Categories -->
<section class="mt-4">
	<div class="flex items-center justify-between px-6 mb-4">
		<h2 class="text-lg font-bold">Categories</h2>
		<button class="text-sm font-semibold text-primary">View All</button>
	</div>
	<div class="flex overflow-x-auto gap-3 px-6 pb-2">
		{#each categories as category}
			<button 
				class={activeCategory === category 
					? "flex-none px-6 py-2.5 rounded-full bg-gradient-main text-white font-semibold text-sm" 
					: "flex-none px-6 py-2.5 rounded-full bg-white dark:bg-slate-800 text-slate-600 dark:text-slate-300 font-medium text-sm soft-shadow"}
				on:click={() => activeCategory = category}
			>
				{category}
			</button>
		{/each}
	</div>
</section>

<!-- Products Grid -->
<main class="px-6 mt-8">
	<div class="grid grid-cols-2 gap-4">
		{#each products as product}
			<div class="bg-white dark:bg-slate-800 rounded-[2rem] p-3 soft-shadow relative group">
				<button class="absolute top-4 right-4 z-10 w-8 h-8 flex items-center justify-center rounded-full bg-white/80 dark:bg-slate-700/80 ios-blur">
					<span class="material-icons-round text-lg {product.liked ? 'text-pink-500' : 'text-slate-400'}">
						{product.liked ? 'favorite' : 'favorite_border'}
					</span>
				</button>
				<div class="aspect-square rounded-[1.5rem] bg-slate-50 dark:bg-slate-700 overflow-hidden mb-4">
					<img 
						alt={product.name}
						class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-500" 
						src={product.image}
					/>
				</div>
				<div class="px-2 pb-2">
					<h3 class="text-sm font-bold text-slate-800 dark:text-slate-100 truncate">{product.name}</h3>
					<p class="text-xs text-slate-500 dark:text-slate-400 mb-2">{product.description}</p>
					<div class="flex items-center justify-between">
						<span class="text-lg font-extrabold text-gradient">${product.price.toFixed(2)}</span>
						<button class="w-8 h-8 rounded-full bg-slate-900 dark:bg-slate-100 flex items-center justify-center text-white dark:text-slate-900">
							<span class="material-icons-round text-base">add</span>
						</button>
					</div>
				</div>
			</div>
		{/each}
	</div>
</main>

<!-- Bottom Navigation -->
<nav class="fixed bottom-6 left-6 right-6 h-20 bg-white/80 dark:bg-slate-800/80 ios-blur rounded-[2.5rem] soft-shadow z-50 flex items-center justify-around px-4 border border-white/20">
	<button class="flex flex-col items-center justify-center text-primary">
		<span class="material-icons-round">home</span>
		<span class="text-[10px] font-bold mt-1">Home</span>
	</button>
	<button class="flex flex-col items-center justify-center text-slate-400 dark:text-slate-500">
		<span class="material-icons-round">shopping_bag</span>
		<span class="text-[10px] font-bold mt-1">Shop</span>
	</button>
	<button class="flex flex-col items-center justify-center text-slate-400 dark:text-slate-500">
		<span class="material-icons-round">favorite_border</span>
		<span class="text-[10px] font-bold mt-1">Wishlist</span>
	</button>
	<button class="flex flex-col items-center justify-center text-slate-400 dark:text-slate-500">
		<span class="material-icons-round">person_outline</span>
		<span class="text-[10px] font-bold mt-1">Profile</span>
	</button>
</nav>

<!-- Background Decorative Glows -->
<div class="fixed top-[-10%] right-[-10%] w-[300px] h-[300px] bg-primary/5 rounded-full blur-[80px] -z-10 pointer-events-none"></div>
<div class="fixed bottom-[10%] left-[-20%] w-[350px] h-[350px] bg-purple-500/5 rounded-full blur-[100px] -z-10 pointer-events-none"></div>
