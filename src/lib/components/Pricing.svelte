<script lang="ts">
  import { Button } from "$lib/components/ui/button";
  import {
    Card,
    CardContent,
    CardDescription,
    CardFooter,
    CardHeader,
    CardTitle,
  } from "$lib/components/ui/card";
  import { Check } from "lucide-svelte";

  interface PlanProps {
    title: string;
    popular: boolean;
    price: number;
    description: string;
    buttonText: string;
    benefitList: string[];
  }

  const plans: PlanProps[] = [
    {
      title: "Free",
      popular: false,
      price: 0,
      description:
        "Lorem ipsum dolor sit, amet ipsum consectetur adipisicing elit.",
      buttonText: "Start Free Trial",
      benefitList: [
        "1 team member",
        "1 GB storage",
        "Upto 2 pages",
        "Community support",
        "AI assistance",
      ],
    },
    {
      title: "Premium",
      popular: true,
      price: 45,
      description:
        "Lorem ipsum dolor sit, amet ipsum consectetur adipisicing elit.",
      buttonText: "Get Started",
      benefitList: [
        "4 team member",
        "8 GB storage",
        "Upto 6 pages",
        "Priority support",
        "AI assistance",
      ],
    },
    {
      title: "Enterprise",
      popular: false,
      price: 120,
      description:
        "Lorem ipsum dolor sit, amet ipsum consectetur adipisicing elit.",
      buttonText: "Contact Us",
      benefitList: [
        "10 team member",
        "20 GB storage",
        "Upto 10 pages",
        "Phone & email support",
        "AI assistance",
      ],
    },
  ];
</script>

<section class="container py-16 sm:py-32">
  <h2 class="text-lg text-primary text-center mb-2 tracking-wider">
    Pricing
  </h2>

  <h2 class="text-3xl md:text-4xl text-center font-bold mb-4">
    Get unlimited access
  </h2>

  <h3 class="md:w-1/2 mx-auto text-xl text-center text-muted-foreground pb-14">
    Lorem ipsum dolor sit amet consectetur adipisicing reiciendis.
  </h3>

  <!-- Mobile First Layout -->
  <div class="block lg:hidden space-y-6">
    {#each plans as { title, popular, price, description, buttonText, benefitList }}
      <div class="relative">
        <Card class={popular ? 'popular-mobile' : ''}>
          {#if popular}
            <div class="absolute -top-4 left-1/2 -translate-x-1/2">
              <span class="bg-primary text-primary-foreground text-xs sm:text-sm font-medium px-3 sm:px-4 py-1 rounded-full whitespace-nowrap">
                Most Popular
              </span>
            </div>
          {/if}
          <CardHeader>
            <CardTitle class="pb-2 text-lg sm:text-xl">
              {title}
            </CardTitle>

            <CardDescription class="pb-4 text-sm sm:text-base">{description}</CardDescription>

            <div>
              <span class="text-2xl sm:text-3xl font-bold">${price}</span>
              <span class="text-muted-foreground text-sm sm:text-base"> /month</span>
            </div>
          </CardHeader>

          <CardContent>
            <div class="space-y-3 sm:space-y-4">
              {#each benefitList as benefit}
                <span class="flex items-center text-sm sm:text-base">
                  <Check class="text-primary mr-2 h-4 w-4 sm:h-5 sm:w-5" />
                  <span>{benefit}</span>
                </span>
              {/each}
            </div>
          </CardContent>

          <CardFooter>
            <Button 
              variant={popular ? "default" : "secondary"}
              class="w-full"
            >
              {buttonText}
            </Button>
          </CardFooter>
        </Card>
      </div>
    {/each}
  </div>

  <!-- Desktop Layout -->
  <div class="hidden lg:grid lg:grid-cols-3 gap-8 relative">
    {#each plans as { title, popular, price, description, buttonText, benefitList }}
      <div class="relative {popular ? 'scale-110 hover:scale-112 z-10' : 'hover:scale-105'} transition-all duration-200">
        <Card class={popular ? 'popular-desktop' : 'hover:border-primary/50'}>
          {#if popular}
            <div class="absolute -top-4 left-1/2 -translate-x-1/2">
              <span class="bg-primary text-primary-foreground text-sm font-medium px-4 py-1 rounded-full whitespace-nowrap shadow-lg">
                Most Popular
              </span>
            </div>
          {/if}
          <CardHeader>
            <CardTitle class="pb-2 text-lg sm:text-xl">
              {title}
            </CardTitle>

            <CardDescription class="pb-4 text-sm sm:text-base">{description}</CardDescription>

            <div>
              <span class="text-2xl sm:text-3xl font-bold">${price}</span>
              <span class="text-muted-foreground text-sm sm:text-base"> /month</span>
            </div>
          </CardHeader>

          <CardContent>
            <div class="space-y-3 sm:space-y-4">
              {#each benefitList as benefit}
                <span class="flex items-center text-sm sm:text-base">
                  <Check class="text-primary mr-2 h-4 w-4 sm:h-5 sm:w-5" />
                  <span>{benefit}</span>
                </span>
              {/each}
            </div>
          </CardContent>

          <CardFooter>
            <Button 
              variant={popular ? "default" : "secondary"}
              class="w-full"
            >
              {buttonText}
            </Button>
          </CardFooter>
        </Card>
      </div>
    {/each}
  </div>
</section>

<style>
    @reference "../../app.css";
  .popular-mobile {
    @apply relative border-primary border-2 shadow-md bg-card scale-[1.02] my-8 ring-2 ring-primary/50 ring-offset-2 ring-offset-background;
  }
  
  .popular-desktop {
    @apply relative border-primary border-2 shadow-2xl bg-card transform-gpu ring-2 ring-primary/50 ring-offset-4 ring-offset-background;
  }
  
  :global(.dark) .popular-desktop {
    @apply shadow-primary/20 ring-primary/40;
  }
</style>