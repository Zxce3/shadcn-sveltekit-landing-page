<script lang="ts">
  import { Card, CardContent, CardHeader, CardTitle } from "$lib/components/ui/card";
  import {
    Sparkle,
    Tag,
    Paintbrush,
    Blocks,
    LineChart,
    Wallet,
  } from "lucide-svelte";

  interface BenefitsProps {
    icon: 'sparkle' | 'tag' | 'paintbrush' | 'blocks' | 'lineChart' | 'wallet';
    title: string;
    description: string;
  }

  const benefitList: BenefitsProps[] = [
    {
      icon: "blocks",
      title: "Build Brand Trust",
      description:
        "Lorem ipsum dolor sit amet consectetur adipisicing elit. A odio velit cum aliquam. Natus consectetur dolores.",
    },
    {
      icon: "lineChart",
      title: "More Leads",
      description:
        "Lorem ipsum dolor sit amet consectetur adipisicing elit. A odio velit cum aliquam, natus consectetur.",
    },
    {
      icon: "wallet",
      title: "Higher Conversions",
      description:
        "Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus consectetur. A odio velit cum aliquam",
    },
    {
      icon: "sparkle",
      title: "Test Marketing Ideas",
      description:
        "Lorem ipsum dolor sit amet consectetur adipisicing elit. A odio velit cum aliquam. Natus consectetur dolores.",
    },
  ];

  const iconMap = {
    sparkle: Sparkle,
    tag: Tag,
    paintbrush: Paintbrush,
    blocks: Blocks,
    lineChart: LineChart,
    wallet: Wallet,
  };
</script>

<section id="benefits" class="container py-24 sm:py-32">
  <div class="grid lg:grid-cols-2 place-items-center lg:gap-24">
    <div>
      <h2 class="text-lg text-primary mb-2 tracking-wider">Benefits</h2>
      <h2 class="text-3xl md:text-4xl font-bold mb-4">
        Your Shortcut to Success
      </h2>
      <p class="text-xl text-muted-foreground mb-8">
        Lorem ipsum dolor sit amet consectetur, adipisicing elit. Non ducimus
        reprehenderit architecto rerum similique facere odit deleniti
        necessitatibus quo quae.
      </p>
    </div>

    <div class="grid lg:grid-cols-2 gap-4 w-full">
      {#each benefitList as { icon, title, description }, index}
        <Card class="bg-muted/50 dark:bg-card hover:bg-background dark:hover:bg-background transition-all delay-75 group/number">
          <CardHeader>
            <div class="flex justify-between">
              <svelte:component 
                this={iconMap[icon]} 
                class="size-8 mb-6 text-primary"
              />
              <span class="text-5xl text-muted-foreground/15 font-medium transition-all delay-75 group-hover/number:text-muted-foreground/30">
                0{index + 1}
              </span>
            </div>
            <CardTitle>{title}</CardTitle>
          </CardHeader>

          <CardContent class="text-muted-foreground">
            {description}
          </CardContent>
        </Card>
      {/each}
    </div>
  </div>
</section>
