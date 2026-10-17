<script setup>
import { ref } from "vue";
import { Head } from "@inertiajs/vue3";
import emailjs from "@emailjs/browser";

const isExpanded = ref(false);

// Contact form
const email = ref("");
const message = ref("");
const sending = ref(false);
const status = ref("");

// Send email using EmailJS
async function sendEmail() {
    if (!email.value.trim() || !message.value.trim()) {
        status.value = "Please fill in all fields.";
        return;
    }

    sending.value = true;
    status.value = "";

    try {
        await emailjs.send(
            "service_om0pa7w",
            "template_bw1l2pf",
            {
                name: "Portfolio Visitor",
                email: email.value,
                title: "Contact Form Message",
                message: message.value,
            },
            {
                publicKey: "2wdmFzwIEDA6CM0D0",
            },
        );

        status.value = "Message sent successfully!";
        email.value = "";
        message.value = "";
    } catch (error) {
        console.error("EmailJS error:", error);
        status.value = "Message could not be sent. Please try again.";
    } finally {
        sending.value = false;
    }
}

const navLinks = [
    { name: "Home", href: "#home" },
    { name: "About", href: "#about" },
    { name: "Pricing", href: "#pricing" },
    { name: "Team", href: "#team" },
    { name: "Services", href: "#services" },
    { name: "Contact", href: "#contact" },
];

const pricingPlans = [
    {
        name: "Basic",
        price: "Free",
        subtitle: "Good for beginners",
        features: [
            "1 Website",
            "1GB Storage",
            "10GB Bandwidth/month",
            "2 Users per Project",
            "Ticket Support",
            "6 Hour Support",
        ],
    },
    {
        name: "Standard",
        price: "$310",
        subtitle: "Good for growing teams",
        features: [
            "Up to 5 Websites",
            "5GB Storage",
            "30GB Bandwidth/month",
            "2 Users per Project",
            "Email Support",
            "12 Hour Support",
        ],
    },
    {
        name: "Professional",
        price: "$530",
        subtitle: "For professional projects",
        features: [
            "Up to 10 Websites",
            "20GB Storage",
            "100GB Bandwidth/month",
            "10 Users per Project",
            "Priority Email Support",
            "24 Hour Support",
        ],
    },
];

const team = [
    {
        name: "Md. Mahim",
        role: "MERN Stack Developer",
        image: "/images/team/mahim.jpeg",
        bio: "Focused on building modern web applications with MongoDB, Express, React and Node.js.",
        github: "https://github.com/",
        linkedin: "https://linkedin.com/",
        facebook: "https://facebook.com/",
    },
    {
        name: "Md. Sabit Parbez",
        role: "Ethical Hacker",
        image: "/images/team/sabit.jpeg",
        bio: "Interested in cybersecurity, security testing and helping improve digital safety.",
        github: "https://github.com/",
        linkedin: "https://linkedin.com/",
        facebook: "https://facebook.com/",
    },
    {
        name: "Arafat Islam",
        role: "HVAC Engineer",
        image: "/images/team/rahat.jpeg",
        bio: "Interested in engineering solutions, system maintenance and technical problem-solving.",
        github: "https://github.com/",
        linkedin: "https://linkedin.com/",
        facebook: "https://facebook.com/",
    },
    {
        name: "Md. Hosen",
        role: "Sales Executive",
        image: "/images/team/hosen.jpeg",
        bio: "Focused on customer communication, building relationships and providing helpful service.",
        github: "https://github.com/",
        linkedin: "https://linkedin.com/",
        facebook: "https://facebook.com/",
    },
];

const services = [
    {
        icon: "fa-solid fa-pen-nib",
        title: "Branding",
        description:
            "Build a memorable brand identity through consistent visuals, clear messaging and meaningful customer experiences.",
    },
    {
        icon: "fa-solid fa-palette",
        title: "Designing",
        description:
            "Create attractive, accessible and user-friendly interfaces for websites and digital products.",
    },
    {
        icon: "fa-solid fa-code",
        title: "Development",
        description:
            "Develop responsive websites and web applications with clean code and modern development practices.",
    },
    {
        icon: "fa-solid fa-rocket",
        title: "Innovation",
        description:
            "Turn creative ideas into practical digital solutions with a focus on performance and usability.",
    },
];
</script>

<template>
    <Head>
        <title>| Portfolio</title>

        <link rel="icon" type="image/jpeg" href="/images/Murad.jpg" />
    </Head>

    <div class="min-h-screen overflow-hidden bg-white font-sans text-slate-800">
        <!-- NAVBAR -->
        <header
            class="sticky top-0 z-50 border-b border-slate-200 bg-gray-200 shadow-sm backdrop-blur"
        >
            <nav
                class="mx-auto flex max-w-7xl items-center justify-between px-5 py-4 lg:px-8"
            >
                <a
                    href="#home"
                    class="text-2xl font-extrabold tracking-tight sm:text-3xl"
                >
                    <span class="text-blue-600">Prism Tech</span> BD
                </a>

                <div class="hidden items-center gap-6 lg:flex">
                    <a
                        v-for="link in navLinks"
                        :key="link.name"
                        :href="link.href"
                        class="text-sm font-semibold text-slate-600 transition hover:text-blue-600"
                    >
                        {{ link.name }}
                    </a>
                </div>

                <a
                    href="#contact"
                    class="rounded-full bg-blue-600 px-5 py-3 text-sm font-semibold text-white transition hover:bg-blue-700"
                >
                    Hire Me
                </a>
            </nav>

            <div
                class="flex flex-wrap justify-center gap-x-5 gap-y-3 border-t border-slate-100 px-3 py-3 lg:hidden"
            >
                <a
                    v-for="link in navLinks"
                    :key="link.name"
                    :href="link.href"
                    class="text-xs font-semibold text-slate-600 hover:text-blue-600 sm:text-sm"
                >
                    {{ link.name }}
                </a>
            </div>
        </header>

        <main>
            <!-- HERO / ABOUT -->
            <section
                id="home"
                class="bg-gradient-to-br from-blue-50 via-white to-indigo-50"
            >
                <div
                    class="mx-auto grid max-w-7xl items-center gap-12 px-6 py-16 md:grid-cols-2 md:py-24 lg:gap-20 lg:px-8"
                >
                    <!-- Profile -->
                    <div class="flex flex-col items-center">
                        <div class="relative">
                            <div
                                class="absolute -inset-4 rounded-[2rem] bg-blue-200/50 blur-xl transition duration-500 group-hover:bg-blue-300/60"
                            ></div>

                            <img
                                src="/images/Murad.jpg"
                                alt="photo"
                                class="group relative h-[240px] w-[140px] cursor-pointer rounded-[2rem] border-4 border-white object-cover shadow-2xl transition-all duration-500 ease-out hover:-translate-y-2 hover:scale-105 hover:shadow-blue-300/50 sm:h-[380px] sm:w-[320px]"
                            />
                        </div>

                        <a
                            href="/images/pdf/Murad cv(1).pdf"
                            target="_blank"
                            rel="noopener noreferrer"
                            class="mt-8 inline-flex items-center gap-3 rounded-xl bg-blue-600 px-7 py-4 font-semibold text-white shadow-lg transition hover:-translate-y-1 hover:bg-blue-700"
                        >
                            <i class="fa-solid fa-download"></i>
                            Download CV
                        </a>
                    </div>

                    <!-- About -->
                    <div
                        class="border-2 rounded-xl border-black p-3"
                        id="about"
                    >
                        <div class="flex justify-center items-center">
                            <span
                                class="inline-flex items-center gap-2 rounded-full bg-blue-100 px-4 py-2 text-2xl font-semibold text-blue-500"
                            >
                                ABOUT ME
                            </span>
                        </div>

                        <!-- <h1 class="mt-6 text-4xl font-extrabold leading-tight tracking-tight text-slate-900 sm:text-6xl">
                            Hello, I'm
                            <span class="text-blue-600">Md. Eyasin</span>
                        </h1> -->

                        <!-- <h2 class="mt-4 text-2xl font-bold text-slate-600 sm:text-3xl">
                            Aspiring Web Developer
                        </h2> -->

                        <p
                            class="mt-6 text-justify text-base leading-8 text-slate-600 sm:text-lg"
                        >
                            Hello! I’m
                            <span class="text-blue-500 font-bold"
                                >Md. Eyasin,</span
                            >
                            from Bhola, and I am a Diploma student in Computer
                            Science & Technology at Bhola Government Polytechnic
                            Institute. I am passionate about technology, web
                            development, software development, and learning new
                            technologies.
                        </p>

                        <p
                            class="mt-4 text-justify text-base leading-8 text-slate-600 sm:text-lg"
                        >
                            I completed my internship at BD Calling Academy,
                            where I gained practical knowledge and experience in
                            a professional working environment. During my
                            internship, I developed my technical, communication,
                            teamwork, and problem-solving skills.
                        </p>

                        <div
                            v-if="isExpanded"
                            class="mt-4 space-y-4 text-justify text-base leading-8 text-slate-600 sm:text-lg"
                        >
                            <p>
                                I am highly motivated to build my career in the
                                Information Technology sector. I enjoy learning
                                new technologies, developing creative solutions,
                                and working on challenging projects.
                            </p>

                            <p>
                                My goal is to build a successful career as a
                                skilled Software/Web Developer. I want to
                                continuously improve my technical skills, work
                                on real-world projects, and contribute to an
                                innovative organization through my knowledge,
                                creativity, and dedication.
                            </p>
                        </div>

                        <div class="mt-6 flex justify-center">
                            <button
                                type="button"
                                @click="isExpanded = !isExpanded"
                                :aria-expanded="isExpanded"
                                class="rounded-xl border-2 border-blue-600 bg-blue-600 px-6 py-3 font-semibold text-white shadow-md transition-all duration-300 hover:scale-105 hover:border-blue-700 hover:bg-blue-700 hover:text-white hover:shadow-lg active:scale-95"
                            >
                                {{
                                    isExpanded ? "Show Less ↑" : "Learn More ↓"
                                }}
                            </button>
                        </div>
                        <div
                            class="mt-[25px] flex flex-wrap gap-4 justify-center"
                        >
                            <a
                                href="https://github.com/mdmurad12"
                                target="_blank"
                                rel="noopener noreferrer"
                                aria-label="GitHub"
                                class="flex h-12 w-12 items-center justify-center rounded-full bg-white text-xl text-slate-700 shadow transition hover:bg-blue-600 hover:text-white"
                            >
                                <i class="fa-brands fa-github"></i>
                            </a>
                            <a
                                href="https://www.linkedin.com/in/md-murad-a51a95383?utm_source=share_via&utm_content=profile&utm_medium=member_android"
                                target="_blank"
                                aria-label="LinkedIn"
                                class="flex h-12 w-12 items-center justify-center rounded-full bg-white text-xl text-slate-700 shadow transition hover:bg-blue-600 hover:text-white"
                            >
                                <i class="fa-brands fa-linkedin-in"></i>
                            </a>
                            <a
                                href="https://www.facebook.com/mdmurad7464"
                                target="_blank"
                                rel="noopener noreferrer"
                                aria-label="Facebook"
                                class="flex h-12 w-12 items-center justify-center rounded-full bg-white text-xl text-slate-700 shadow transition hover:bg-blue-600 hover:text-white"
                            >
                                <i class="fa-brands fa-facebook-f"></i>
                            </a>
                            <a
                                href="https://x.com/murad278b"
                                target="_blank"
                                rel="noopener noreferrer"
                                aria-label="X / Twitter"
                                class="flex h-12 w-12 items-center justify-center rounded-full bg-white text-xl text-slate-700 shadow transition hover:bg-sky-500 hover:text-white"
                            >
                                <i class="fa-brands fa-x-twitter"></i>
                            </a>
                            <a
                                href="https://www.instagram.com/mdmurad7644/"
                                target="_blank"
                                rel="noopener noreferrer"
                                aria-label="Instagram"
                                class="flex h-12 w-12 items-center justify-center rounded-full bg-white text-xl text-slate-700 shadow transition hover:bg-pink-600 hover:text-white"
                            >
                                <i class="fa-brands fa-instagram"></i>
                            </a>
                            <a
                                href="https://t.me/mmurad27"
                                target="_blank"
                                rel="noopener noreferrer"
                                aria-label="Telegram"
                                class="flex h-12 w-12 items-center justify-center rounded-full bg-white text-xl text-slate-700 shadow transition hover:bg-sky-500 hover:text-white"
                            >
                                <i class="fa-brands fa-telegram"></i>
                            </a>
                            <a
                                href="https://www.youtube.com/@Seeker9gr"
                                target="_blank"
                                rel="noopener noreferrer"
                                aria-label="YouTube"
                                class="flex h-12 w-12 items-center justify-center rounded-full bg-white text-xl text-slate-700 shadow transition hover:bg-red-600 hover:text-white"
                            >
                                <i class="fa-brands fa-youtube"></i>
                            </a>
                        </div>
                    </div>
                </div>
            </section>

            <!-- PRICING -->
            <section id="pricing" class="bg-slate-50 px-6 py-20 lg:px-8">
                <div class="mx-auto max-w-7xl">
                    <div class="mx-auto mb-14 max-w-2xl text-center">
                        <!-- <span
                            class="text-sm font-bold uppercase tracking-[0.2em] text-blue-600"
                        >
                            Pricing Plans
                        </span> -->
                        <h2
                            id="price_plan"
                            class="mt-3 text-3xl font-extrabold text-blue-300 sm:text-5xl text-shadow-[2px_4px_3px_black]"
                        >
                            Choose Your Plan
                        </h2>
                        <p class="mt-4 leading-7 text-slate-800">
                            Flexible options for different project needs.
                        </p>
                    </div>

                    <div
                        class="grid gap-8 md:grid-cols-2 lg:grid-cols-3 mt-[-20px]"
                    >
                        <article
                            v-for="(plan, index) in pricingPlans"
                            :key="plan.name"
                            class="relative flex flex-col rounded-3xl border border-slate-200 bg-white p-6 shadow-sm transition duration-300 hover:-translate-y-2 hover:shadow-xl"
                            :class="
                                index === 1
                                    ? 'border-blue-600 ring-2 ring-blue-600'
                                    : ''
                            "
                        >
                            <span
                                v-if="index === 1"
                                class="absolute -top-4 left-1/2 -translate-x-1/2 whitespace-nowrap rounded-full bg-blue-600 px-5 py-2 text-xs font-bold text-white"
                            >
                                POPULAR PLAN
                            </span>

                            <h3
                                class="text-xl text-center font-bold text-slate-800"
                            >
                                {{ plan.name }}
                            </h3>

                            <div
                                class="mt-4 flex justify-center items-baseline gap-2"
                            >
                                <span
                                    class="text-4xl font-extrabold text-slate-900"
                                >
                                    {{ plan.price }}
                                </span>

                                <!-- <span
                                    v-if="index !== 0"
                                    class="text-sm text-slate-500"
                                >
                                    / project
                                </span> -->
                            </div>

                            <p class="mt-2 text-sm text-center text-slate-500">
                                {{ plan.subtitle }}
                            </p>

                            <div class="my-5 h-px bg-slate-200"></div>

                            <ul class="flex-1 space-y-3">
                                <li
                                    v-for="feature in plan.features"
                                    :key="feature"
                                    class="flex items-start gap-3 text-sm text-slate-600"
                                >
                                    <i
                                        class="fa-solid fa-circle-check mt-1 text-blue-600"
                                    ></i>

                                    <span>{{ feature }}</span>
                                </li>
                            </ul>

                            <a
                                href="#contact"
                                class="mt-6 block rounded-xl bg-blue-600 px-5 py-3 text-center font-bold text-white transition duration-300 hover:bg-blue-700"
                            >
                                Choose Plan
                            </a>
                        </article>
                    </div>
                </div>
            </section>

            <!-- TEAM -->
            <section id="team" class="bg-white px-6 py-20 lg:px-8">
                <div class="mx-auto max-w-7xl">
                    <div class="mx-auto mb-14 max-w-2xl text-center">
                        <span
                            id="team_our"
                            class="text-sm font-bold uppercase tracking-[0.2em] text-blue-600"
                        >
                            Our People
                        </span>
                        <h2
                            class="mt-[-40px] text-3xl font-extrabold text-slate-900 sm:text-5xl"
                        >
                            Meet Our Team
                        </h2>
                        <p class="mt-4 leading-7 text-slate-500">
                            A team with different skills, ideas and professional
                            interests.
                        </p>
                    </div>

                    <div
                        class="grid gap-8 sm:grid-cols-2 lg:grid-cols-4 mt-[-30px]"
                    >
                        <article
                            v-for="member in team"
                            :key="member.name"
                            class="h-[430px] overflow-hidden rounded-2xl border border-slate-200 bg-white text-center shadow-sm transition duration-300 hover:-translate-y-2 hover:shadow-xl"
                        >
                            <div
                                class="bg-gradient-to-br from-blue-50 to-indigo-100 px-5 pb-5 pt-7"
                            >
                                <img
                                    :src="member.image"
                                    :alt="member.name"
                                    class="mx-auto h-28 w-28 rounded-full border-4 border-white object-cover shadow-md"
                                    loading="lazy"
                                />
                            </div>

                            <div class="p-6">
                                <h3 class="text-lg font-bold text-slate-800">
                                    {{ member.name }}
                                </h3>

                                <p
                                    class="mt-2 text-sm font-semibold text-blue-600"
                                >
                                    {{ member.role }}
                                </p>

                                <p
                                    class="mt-3 text-sm leading-6 text-slate-500"
                                >
                                    {{ member.bio }}
                                </p>

                                <div
                                    class="mt-5 flex justify-center gap-5 border-t border-slate-100 pt-4"
                                >
                                    <a
                                        :href="member.facebook"
                                        target="_blank"
                                        rel="noopener noreferrer"
                                        aria-label="Facebook"
                                        class="text-xl text-slate-500 transition hover:text-blue-600"
                                    >
                                        <i class="fa-brands fa-facebook-f"></i>
                                    </a>

                                    <a
                                        :href="member.github"
                                        target="_blank"
                                        rel="noopener noreferrer"
                                        aria-label="GitHub"
                                        class="text-xl text-slate-500 transition hover:text-blue-600"
                                    >
                                        <i class="fa-brands fa-github"></i>
                                    </a>

                                    <a
                                        :href="member.linkedin"
                                        target="_blank"
                                        rel="noopener noreferrer"
                                        aria-label="LinkedIn"
                                        class="text-xl text-slate-500 transition hover:text-blue-600"
                                    >
                                        <i class="fa-brands fa-linkedin-in"></i>
                                    </a>
                                </div>
                            </div>
                        </article>
                    </div>
                </div>
            </section>

            <!-- SERVICES -->
            <section id="services" class="bg-slate-50 px-6 py-20 lg:px-8">
                <div class="mx-auto max-w-7xl">
                    <div class="mx-auto mb-14 max-w-2xl text-center">
                        <span
                            class="text-sm font-bold uppercase tracking-[0.2em] text-blue-600"
                        >
                            What We Do
                        </span>
                        <h2
                            class="mt-3 text-3xl font-extrabold text-slate-900 sm:text-5xl"
                        >
                            Services We Provide
                        </h2>
                        <p class="mt-4 leading-7 text-slate-500">
                            Creative ideas and practical solutions for the
                            digital world.
                        </p>
                    </div>

                    <div class="grid gap-7 sm:grid-cols-2 lg:grid-cols-4">
                        <article
                            v-for="service in services"
                            :key="service.title"
                            class="group rounded-2xl border border-slate-200 bg-white p-7 text-center shadow-sm transition duration-300 hover:-translate-y-2 hover:border-blue-200 hover:shadow-xl"
                        >
                            <div
                                class="mx-auto flex h-14 w-14 items-center justify-center rounded-2xl bg-blue-50 text-2xl text-blue-600 transition group-hover:bg-blue-600 group-hover:text-white"
                            >
                                <i :class="service.icon"></i>
                            </div>

                            <h3 class="mt-6 text-xl font-bold text-slate-800">
                                {{ service.title }}
                            </h3>

                            <p class="mt-4 text-sm leading-7 text-slate-500">
                                {{ service.description }}
                            </p>
                        </article>
                    </div>
                </div>
            </section>

            <!-- CONTACT CTA -->
            <section
                id="contact"
                class="bg-blue-700 px-6 py-20 text-center text-white"
            >
                <div class="mx-auto max-w-3xl">
                    <span
                        class="text-sm font-bold uppercase tracking-[0.2em] text-blue-200"
                    >
                        Get In Touch
                    </span>
                    <h2 class="mt-4 text-3xl font-extrabold sm:text-5xl">
                        Let's Work Together
                    </h2>
                    <p class="mx-auto mt-5 max-w-xl leading-8 text-blue-100">
                        Have a project, job opportunity or an idea to discuss? I
                        would be happy to hear from you.
                    </p>

                    <form @submit.prevent="sendEmail" class="space-y-4 mt-6">
                        <div>
                            <!-- <label for="email" class="mb-2 block font-medium">
                                Your Email
                            </label> -->

                            <input
                                id="email"
                                v-model="email"
                                type="email"
                                placeholder="Enter your email"
                                required
                                class="w-full text-black rounded-lg border border-gray-300 px-4 py-3 outline-none focus:border-blue-500"
                            />
                        </div>

                        <div>
                            <label for="message" class="mb-2 block font-medium">
                                Your Message
                            </label>

                            <textarea
                                id="message"
                                v-model="message"
                                rows="3"
                                placeholder="Write your message..."
                                required
                                class="w-full text-black rounded-lg border border-gray-300 px-4 py-3 outline-none focus:border-blue-500"
                            ></textarea>
                        </div>

                        <button
                            type="submit"
                            :disabled="sending"
                            class="rounded-lg bg-blue-600 px-6 py-3 font-semibold text-white transition hover:bg-blue-700 disabled:cursor-not-allowed disabled:opacity-50"
                        >
                            {{ sending ? "Sending..." : "Send Message" }}
                        </button>

                        <p v-if="status" role="status" aria-live="polite">
                            {{ status }}
                        </p>
                    </form>
                </div>
            </section>
        </main>

        <!-- FOOTER -->
        <footer class="bg-slate-950 px-6 pb-6 pt-14 text-slate-300 lg:px-8">
            <div
                class="mx-auto grid max-w-7xl gap-10 sm:grid-cols-2 lg:grid-cols-4"
            >
                <div>
                    <a href="#home" class="text-2xl font-extrabold text-white">
                        <span class="text-blue-400">Md.</span> Eyasin.
                    </a>
                    <p
                        class="mt-5 max-w-xs text-justify text-sm leading-7 text-slate-400"
                    >
                        Aspiring web developer passionate about technology,
                        creative solutions and continuous learning.
                    </p>

                    <div class="mt-5 flex items-center justify-center gap-10">
                        <a
                            href="https://github.com/mdmurad12"
                            target="_blank"
                            rel="noopener noreferrer"
                            aria-label="GitHub"
                            class="text-xl transition hover:text-blue-400"
                        >
                            <i class="fa-brands fa-github"></i>
                        </a>

                        <a
                            href="https://www.linkedin.com/in/md-murad-a51a95383"
                            target="_blank"
                            rel="noopener noreferrer"
                            aria-label="LinkedIn"
                            class="text-xl transition hover:text-blue-400"
                        >
                            <i class="fa-brands fa-linkedin-in"></i>
                        </a>

                        <a
                            href="https://www.facebook.com/mdmurad7464"
                            target="_blank"
                            rel="noopener noreferrer"
                            aria-label="Facebook"
                            class="text-xl transition hover:text-blue-400"
                        >
                            <i class="fa-brands fa-facebook-f"></i>
                        </a>

                        <a
                            href="https://t.me/mmurad27"
                            target="_blank"
                            rel="noopener noreferrer"
                            aria-label="Telegram"
                            class="text-xl transition hover:text-blue-400"
                        >
                            <i class="fa-brands fa-telegram"></i>
                        </a>
                    </div>
                </div>

                <div>
                    <h3 class="font-bold text-white">Quick Links</h3>
                    <ul class="mt-5 space-y-3 text-sm">
                        <li>
                            <a href="#home" class="hover:text-blue-400">Home</a>
                        </li>
                        <li>
                            <a href="#about" class="hover:text-blue-400"
                                >About Me</a
                            >
                        </li>
                        <li>
                            <a href="#pricing" class="hover:text-blue-400"
                                >Pricing</a
                            >
                        </li>
                        <li>
                            <a href="#team" class="hover:text-blue-400"
                                >Our Team</a
                            >
                        </li>
                        <li>
                            <a href="#services" class="hover:text-blue-400"
                                >Services</a
                            >
                        </li>
                    </ul>
                </div>

                <div>
                    <h3 class="font-bold text-white">My Services</h3>
                    <ul class="mt-5 space-y-3 text-sm">
                        <li>Web Development</li>
                        <li>Website Design</li>
                        <li>Responsive UI</li>
                        <li>Software Development</li>
                        <li>Creative Solutions</li>
                    </ul>
                </div>

                <div>
                    <h3 class="font-bold text-white">Contact Information</h3>
                    <ul class="mt-5 space-y-4 text-sm text-slate-400">
                        <li class="flex items-start gap-3">
                            <i
                                class="fa-solid fa-location-dot mt-1 text-blue-400"
                            ></i>
                            <span>Bhola, Barishal, Bangladesh</span>
                        </li>
                        <li class="flex items-start gap-3">
                            <i
                                class="fa-regular fa-envelope mt-1 text-blue-400"
                            ></i>
                            <a
                                href="mailto:your-email@example.com"
                                class="break-all hover:text-blue-400"
                            >
                                mdeyasin27@gmail.com
                            </a>
                        </li>
                        <li class="flex items-start gap-3">
                            <i
                                class="fa-regular fa-file-pdf mt-1 text-blue-400"
                            ></i>
                            <a
                                href="/images/pdf/Murad cv(1).pdf"
                                target="_blank"
                                rel="noopener noreferrer"
                                class="hover:text-blue-400"
                            >
                                View My CV
                            </a>
                        </li>
                    </ul>
                </div>
            </div>

            <div
                class="mx-auto mt-12 max-w-7xl border-t border-slate-800 pt-6 text-center text-sm text-slate-500"
            >
                <p>
                    © {{ new Date().getFullYear() }} Md. Eyasin. All rights
                    reserved.
                </p>
                <a
                    href="#home"
                    class="mt-3 inline-block font-medium text-blue-400 hover:text-blue-300"
                >
                    Back to Top ↑
                </a>
            </div>
        </footer>
    </div>
</template>

<style scoped>
#price_plan {
    text-shadow: 2px 4px 5px black;
    margin-top: -60px;
}

#team_our {
    display: inline-block;
    transform: translateY(-50px);
}
</style>
