<script>
    let fullName = '';
    let email = '';
    let phoneNumber = '';
    let message = '';
</script>
<section class=" w-full h-full">
    <h1 class="text-[34px] font-bold  text-gray-800 mb-4">Contact me</h1>
    <p class=" text-gray-600 mb-8 text-[14px]">I will be happy to receive a message from you!</p>
    <form class="max-w-lg ">
        <div class="form-group mb-4">
            <label for="fullName" class="block text-gray-700 font-medium mb-2">Full Name</label>
            <input
                type="text"
                id="fullName"
                bind:value={fullName}
                placeholder="Enter your full name"
                required
                class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500"
            />
        </div>

        <div class="form-group mb-4">
            <label for="email" class="block text-gray-700 font-medium mb-2">Email</label>
            <input
                type="email"
                id="email"
                bind:value={email}
                placeholder="Enter your email"
                required
                class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500"
            />
        </div>

        <div class="form-group mb-4">
            <label for="phoneNumber" class="block text-gray-700 font-medium mb-2">Phone Number</label>
            <input
                type="tel"
                id="phoneNumber"
                bind:value={phoneNumber}
                placeholder="Enter your phone number"
                required
                class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500"
            />
        </div>

        <div class="form-group mb-4">
            <label for="message" class="block text-gray-700 font-medium mb-2">Message</label>
            <textarea
                id="message"
                bind:value={message}
                placeholder="Enter your message"
                rows="5"
                required
                class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500"
            ></textarea>
        </div>

        <button
            type="submit"
            class="w-full bg-blue-500 text-white font-medium py-2 px-4 rounded-lg hover:bg-blue-600 focus:outline-none focus:ring-2 focus:ring-blue-500"
        >
            Submit
        </button>
    </form>
</section>
