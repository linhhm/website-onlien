<template>
  <section class="py-12 px-6 bg-gradient-to-r from-red-300 to-orange-200 text-blue-700 text-center">
    <h2 class="text-4xl font-bold">🎉 Sự Kiện Khuyến Mãi Lớn 🎉</h2>
    <p class="text-lg mt-2">Cơ hội mua sắm với giá cực sốc! Nhanh tay trước khi hết hạn!</p>

    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 mt-8">
      <div
        v-for="event in events"
        :key="event.id"
        class="p-6 bg-white text-black rounded-lg shadow-lg relative transform hover:scale-105 transition duration-300"
      >
        <span class="absolute top-2 right-2 bg-yellow-300 text-black px-3 py-1 rounded-full font-bold">
          {{ event.discount }}% OFF
        </span>
        <img
          :src="event.image"
          :alt="event.title"
          class="w-full h-48 object-cover rounded-lg shadow-md"
        >
        <h3 class="mt-4 text-2xl font-semibold">{{ event.title }}</h3>
        <p class="mt-2 text-gray-600">{{ event.description }}</p>
        <p class="text-sm text-red-500 mt-1">⏳ Hết hạn: {{ event.deadline }}</p>
        <p class="mt-2 text-lg font-bold text-red-300">
          {{ event.price }} VND
          <span v-if="event.originalPrice" class="line-through text-gray-500">
            {{ event.originalPrice }} VND
          </span>
        </p>
        <router-link :to="event.link">
          <button class="mt-4 w-full bg-red-600 text-white py-2 rounded-lg hover:bg-red-700 transition">
            {{ event.cta || 'Xem chi tiết' }}
          </button>
        </router-link>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      events: [
        {
          id: 1,
          title: "Black Friday",
          description: "Giảm giá cực sốc lên đến 50%",
          discount: 50,
          price: "14.990.000",
          originalPrice: "29.990.000",
          image: "https://source.unsplash.com/400x300/?shopping",
          link: "/",
          cta: "Xem chi tiết",
          deadline: "30/11/2025"
        },
        {
          id: 2,
          title: "Sale Tết 2025",
          description: "Ưu đãi đặc biệt đón năm mới",
          discount: 30,
          price: "20.990.000",
          originalPrice: "29.990.000",
          image: "https://source.unsplash.com/400x300/?discount",
          link: "/",
          cta: "Xem chi tiết",
          deadline: "01/02/2025"
        },
        {
          id: 3,
          title: "Flash Sale 12.12",
          description: "Chỉ trong hôm nay!",
          discount: 40,
          price: "17.990.000",
          originalPrice: "29.990.000",
          image: "https://source.unsplash.com/400x300/?electronics",
          link: "/",
          cta: "Mua ngay",
          deadline: "12/12/2025"
        }
      ]
    };
  }
};
</script>
