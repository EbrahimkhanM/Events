<script>
  import { createEventDispatcher } from "svelte";
  import { onMount } from "svelte";
  import "./styles.css";
  import profile from "$lib/images/Thumbnail (1).png";
  import profile2 from "$lib/images/Thumbnail (2).png";
  import profile3 from "$lib/images/Thumbnail (3).png";
  import avater1 from "$lib/images/Avatar.png";
  import avater2 from "$lib/images/Avatar (1).png";
  import avater3 from "$lib/images/Avatar (2).png";
  import avater4 from "$lib/images/Avatar (3).png";
  import { Pagination } from "flowbite-svelte";

  import {
    Table,
    TableBody,
    TableBodyCell,
    TableBodyRow,
    TableHead,
    TableHeadCell,
    Checkbox,
    Progressbar,
    Button,
  } from "flowbite-svelte";
  let products = [
    {
      Show: {
        image: profile,
        name: "Jetpack Comedy",
        time: "12:30PM PST",
      },

      Performers: [avater1, avater2, avater3, avater4],
      Seats: {
        progress: 80,
        title: "875/1023",
        tagline: "2 in cart",
      },
      Sale: "$1482",
      Type: "Stand-up",
      Stage: "Main",
      Status: "On sale",
    },
    {
      Show: {
        image: profile2,
        name: "Adrenaline",
        time: "12:30PM PST",
      },

      Performers: [avater1, avater2, avater3, avater4],
      Seats: {
        progress: 49,
        title: "240/500",
        tagline: "2 in cart",
      },
      Sale: "$1482",
      Type: "Stand-up",
      Stage: "Main",
      Status: "Draft",
    },
    {
      Show: {
        image: profile3,
        name: "The Reading Out of Your Notebook",
        time: "12:30PM PST",
      },

      Performers: [avater1, avater2, avater3, avater4],
      Seats: {
        progress: 15,
        title: "15/889",
        tagline: "2 in cart",
      },
      Sale: "$1482",
      Type: "Stand-up",
      Stage: "Main",
      Status: "Scheduled",
    },
    {
      Show: {
        image: profile3,
        name: "The Reading Out of Your Notebook",
        time: "12:30PM PST",
      },

      Performers: [avater1, avater2, avater3, avater4],
      Seats: {
        progress: 15,
        title: "15/889",
        tagline: "2 in cart",
      },
      Sale: "$1482",
      Type: "Stand-up",
      Stage: "Main",
      Status: "Scheduled",
    },
    {
      Show: {
        image: profile3,
        name: "The Reading Out of Your Notebook",
        time: "12:30PM PST",
      },

      Performers: [avater1, avater2, avater3, avater4],
      Seats: {
        progress: 15,
        title: "15/889",
        tagline: "2 in cart",
      },
      Sale: "$1482",
      Type: "Stand-up",
      Stage: "Main",
      Status: "Scheduled",
    },
    {
      Show: {
        image: profile3,
        name: "The Reading Out of Your Notebook",
        time: "12:30PM PST",
      },

      Performers: [avater1, avater2, avater3, avater4],
      Seats: {
        progress: 15,
        title: "15/889",
        tagline: "2 in cart",
      },
      Sale: "$1482",
      Type: "Stand-up",
      Stage: "Main",
      Status: "Scheduled",
    },
    {
      Show: {
        image: profile3,
        name: "The Reading Out of Your Notebook",
        time: "12:30PM PST",
      },

      Performers: [avater1, avater2, avater3, avater4],
      Seats: {
        progress: 15,
        title: "15/889",
        tagline: "2 in cart",
      },
      Sale: "$1482",
      Type: "Stand-up",
      Stage: "Main",
      Status: "Scheduled",
    },
  ];

  const dispatcher = createEventDispatcher();
  let dropdownOpen = false;

  let openDropdownIndex = -1; // Initially no dropdown is open

  const toggleDropdown = (index) => {
    if (openDropdownIndex === index) {
      openDropdownIndex = -1; // Close dropdown if it's already open
    } else {
      openDropdownIndex = index; // Otherwise, open dropdown for the clicked row
    }
  };

  let filteredProducts = [];
  let searchQuery = "";

  const handleSearch = () => {
    filteredProducts = products.filter((product) =>
      product.Show.name.toLowerCase().includes(searchQuery.toLowerCase())
    );
  };
  const handleDelete = (index) => {
    if (index === openDropdownIndex) {
      // Delete the item only if its dropdown is open
      filteredProducts.splice(index, 1);
      openDropdownIndex = -1; // For reset openDropdownIndex after deletion
    }
  };
  function getColor(progress) {
    if (progress > 50) {
      return "green";
    } else if (progress >= 30 && progress <= 50) {
      return "yellow";
    } else {
      return "red";
    }
  }

  onMount(() => {
    filteredProducts = products;
  });
</script>

<div class="app">
  <!-- <Header /> -->

  <main class="bg-[#F5F5F5] h-[100%]">
    <!-- <slot /> -->

    <div class="main-container pt-4">
      <div class="m-3 px-[24px] pt-[14px] pb-[16px] rounded-2xl bg-white">
        <div
          class="flex items-center md:justify-between md:mb-0 mb-[16px] justify-end"
        >
          <div class="md:block hidden">
            <h1 class="text-[20px] leading-5 text-[#08132B]">
              Upcoming events
            </h1>
          </div>
          <div class="mr-3">
            <Button
              class="px-3 py-[10px] bg-[#1C64F2] hover:bg-[#2e487d] transition-all ease-in-out   flex items-center gap-2"
            >
              <svg
                width="24"
                height="24"
                viewBox="0 0 24 24"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  d="M12 4V20"
                  stroke="white"
                  stroke-width="1.5"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                />
                <path
                  d="M4 12H20"
                  stroke="white"
                  stroke-width="1.5"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                />
              </svg>
              <span>Create event</span>
            </Button>
          </div>
        </div>
        <div class="lg:w-[50%] w-full md:block hidden my-[16px]">
          <div>
            <form class="flex items-center gap-[16px]">
              <!-- <Search size="md" /> -->
              <div class="relative w-[70%]">
                <input
                  type="text"
                  class="w-full py-2 pl-10 pr-3 bg-[#F7F7F8] shadow-sm border-[#D4D6D9] border-[1.7px] shadow-input rounded-[8px] focus:outline-none focus:ring-1 focus:ring-blue-500"
                  placeholder="Search"
                  bind:value={searchQuery}
                  on:input={handleSearch}
                />
                <span class="absolute inset-y-0 left-0 flex items-center pl-3">
                  <svg
                    width="20"
                    height="20"
                    viewBox="0 0 20 20"
                    fill="none"
                    xmlns="http://www.w3.org/2000/svg"
                  >
                    <path
                      d="M14.5835 14.5833L18.3335 18.3333"
                      stroke="#666C79"
                      stroke-width="1.5"
                      stroke-linecap="round"
                      stroke-linejoin="round"
                    />
                    <path
                      d="M16.6665 9.16667C16.6665 5.02453 13.3087 1.66667 9.1665 1.66667C5.02437 1.66667 1.6665 5.02453 1.6665 9.16667C1.6665 13.3088 5.02437 16.6667 9.1665 16.6667C13.3087 16.6667 16.6665 13.3088 16.6665 9.16667Z"
                      stroke="#666C79"
                      stroke-width="1.5"
                      stroke-linejoin="round"
                    />
                  </svg>
                </span>
              </div>
              <div>
                <div
                  class="flex items-center cursor-pointer gap-[8px] py-[6px] px-[12px] border-[#D4D6D9] border-[1.7px] rounded-[11px]"
                >
                  <svg
                    width="24"
                    height="24"
                    viewBox="0 0 24 24"
                    fill="none"
                    xmlns="http://www.w3.org/2000/svg"
                  >
                    <path
                      d="M8.85746 12.5061C6.36901 10.6456 4.59564 8.59915 3.62734 7.44867C3.3276 7.09253 3.22938 6.8319 3.17033 6.3728C2.96811 4.8008 2.86701 4.0148 3.32795 3.5074C3.7889 3 4.60404 3 6.23433 3H17.7657C19.396 3 20.2111 3 20.672 3.5074C21.133 4.0148 21.0319 4.8008 20.8297 6.37281C20.7706 6.83191 20.6724 7.09254 20.3726 7.44867C19.403 8.60062 17.6261 10.6507 15.1326 12.5135C14.907 12.6821 14.7583 12.9567 14.7307 13.2614C14.4837 15.992 14.2559 17.4876 14.1141 18.2442C13.8853 19.4657 12.1532 20.2006 11.226 20.8563C10.6741 21.2466 10.0043 20.782 9.93278 20.1778C9.79643 19.0261 9.53961 16.6864 9.25927 13.2614C9.23409 12.9539 9.08486 12.6761 8.85746 12.5061Z"
                      stroke="#1C64F2"
                      stroke-width="1.5"
                      stroke-linecap="round"
                      stroke-linejoin="round"
                    />
                  </svg>
                  <span
                    class="text-[14px] leading-[14px] text-[#1C64F2] hover:text-[#517bce] transition-all ease-in-out font-medium"
                    >Filters</span
                  >
                </div>
              </div>
              <div>
                <div
                  class="flex items-center gap-[8px] cursor-pointer py-[6px] px-[12px] border-[#D4D6D9] border-[1.7px] rounded-[11px]"
                >
                  <span
                    class="text-[14px] leading-[14px] text-[#333B4C] font-medium"
                    >Actions</span
                  >
                  <svg
                    width="24"
                    height="24"
                    viewBox="0 0 24 24"
                    fill="none"
                    xmlns="http://www.w3.org/2000/svg"
                  >
                    <path
                      d="M6 9C6 9 10.4189 15 12 15C13.5812 15 18 9 18 9"
                      stroke="#333B4C"
                      stroke-width="1.5"
                      stroke-linecap="round"
                      stroke-linejoin="round"
                    />
                  </svg>
                </div>
              </div>
            </form>
          </div>
        </div>
        <div class="table-wrapper">
          <Table
            style="width: 100%;"
            class="table-main md:min-w-[1024px] min-w-[340px] "
          >
            <TableHead
              class="text-[#666C79] text-[14px] leading-[14px] !font-normal md:table-header-group hidden"
              style="text-align: left; background-color: #f7f7f8;"
            >
              <TableHeadCell style="width: 71px;" class="py-5 !px-[7px]">
                <Checkbox />
              </TableHeadCell>
              <TableHeadCell
                class="!font-normal py-5 !px-1"
                style="width: 245px;">Show</TableHeadCell
              >
              <TableHeadCell class="!font-normal py-5 !px-1"
                >Performers</TableHeadCell
              >
              <TableHeadCell class="!font-normal py-5 !px-1 "
                >Seats</TableHeadCell
              >
              <TableHeadCell class="!font-normal py-5 !px-1 !pl-7"
                >Sale</TableHeadCell
              >
              <TableHeadCell class="!font-normal py-5 !px-1">Type</TableHeadCell
              >
              <TableHeadCell class="!font-normal py-5 !px-1"
                >Stage</TableHeadCell
              >
              <TableHeadCell class="!font-normal py-5 !px-1"
                >Status</TableHeadCell
              >
            </TableHead>
            <!-- Table Body -->
            <TableBody class="divide-y">
              {#each filteredProducts as product, index}
                <TableBodyRow style="border-bottom: 1px solid #E5E7EB;">
                  <TableBodyCell class="p-0 md:table-cell hidden">
                    <div
                      style="display: flex; gap:7px; align-items: center; justify-content: center;"
                    >
                      <Checkbox />
                      <div style="text-align:center">
                        <span
                          style="display: block; font-size:10px; line-height:14px; color:#666c79"
                          >FRI</span
                        >
                        <span
                          style="display: block; font-size:20px; line-height:20px; color:#1C64F2"
                          >23</span
                        >
                        <span
                          style="display: block; font-size:10px; line-height:14px; color:#666c79"
                          >SEP</span
                        >
                      </div>
                    </div>
                  </TableBodyCell>
                  <TableBodyCell class="p-0">
                    <div class=" flex md:gap-[2px] sm:gap-3 gap-2 py-[13px]">
                      <div style="text-align: center" class=" md:hidden block">
                        <span
                          style="display: block; font-size:10px; line-height:14px; color:#666c79"
                          >FRI</span
                        >
                        <span
                          style="display: block; font-size:20px; line-height:20px; color:#1C64F2"
                          >23</span
                        >
                        <span
                          style="display: block; font-size:10px; line-height:14px; color:#666c79"
                          >SEP</span
                        >
                      </div>
                      <div style="">
                        <img
                          src={product.Show.image}
                          width="48px"
                          class="min-w-[48px] ml-1"
                          alt=""
                        />
                      </div>
                      <div style="margin-left: 10px;">
                        <h2
                          style="font-size:14px; line-height:14px; color:#08132B; margin-bottom:8px"
                        >
                          <!-- {product.Show.name} -->
                          <span
                            style="display: block; max-width: 100%; overflow: hidden; text-overflow: ellipsis; white-space: nowrap;"
                          >
                            {#if product.Show.name.length > 18}
                              {product.Show.name.substr(0, 18) + "..."}
                            {:else}
                              {product.Show.name}
                            {/if}
                          </span>
                        </h2>
                        <div class="md:block hidden">
                          <p
                            style="font-size:12px; line-height:16px; color:#666C79; "
                          >
                            {product.Show.time}
                          </p>
                        </div>
                        <div class="flex md:hidden items-center gap-2">
                          <div class="flex">
                            {#each product.Performers as performer}
                              <img
                                src={performer}
                                alt="img"
                                style="margin-left: -8px"
                              />
                            {/each}
                          </div>
                          {#if product.Status === "On sale"}
                            <div class="rounded-2xl py-1 px-[6px] w-fit">
                              <div
                                class="flex items-center gap-[2.5px] text-[#15A033] text-xs font-semibold text-center"
                              >
                                <svg
                                  width="8"
                                  height="8"
                                  viewBox="0 0 8 8"
                                  fill="none"
                                  xmlns="http://www.w3.org/2000/svg"
                                >
                                  <circle
                                    cx="3.75"
                                    cy="4"
                                    r="3.5"
                                    fill="#15A033"
                                  />
                                </svg>
                                <p class="font-semibold">On Sale</p>
                              </div>
                            </div>
                          {/if}
                          {#if product.Status === "Draft"}
                            <div class=" rounded-2xl py-1 px-[6px] w-fit">
                              <div
                                class="flex items-center gap-[2.5px] text-[#6C2BD9] text-xs font-semibold text-center"
                              >
                                <!-- <span class="green-dot"></span> -->
                                <svg
                                  width="8"
                                  height="8"
                                  viewBox="0 0 8 8"
                                  fill="none"
                                  xmlns="http://www.w3.org/2000/svg"
                                >
                                  <circle
                                    cx="3.75"
                                    cy="4"
                                    r="3.5"
                                    fill="#6C2BD9"
                                  />
                                </svg>
                                <p class="font-semibold">Draft</p>
                              </div>
                            </div>
                          {/if}
                          {#if product.Status === "Scheduled"}
                            <div class=" rounded-2xl py-1 px-[6px] w-fit">
                              <div
                                class="flex items-center gap-[2.5px] text-[#FF922E] text-xs font-semibold text-center"
                              >
                                <!-- <span class="green-dot"></span> -->
                                <svg
                                  width="13"
                                  height="12"
                                  viewBox="0 0 13 12"
                                  fill="none"
                                  xmlns="http://www.w3.org/2000/svg"
                                >
                                  <circle
                                    cx="6.75"
                                    cy="6"
                                    r="3.5"
                                    fill="#FF922E"
                                  />
                                </svg>
                                <p class="font-semibold">Scheduled</p>
                              </div>
                            </div>
                          {/if}
                        </div>
                      </div>
                    </div>
                  </TableBodyCell>
                  <TableBodyCell class="p-0 md:table-cell hidden">
                    <div style="display: flex;">
                      {#each product.Performers as performer}
                        <img
                          src={performer}
                          alt="img"
                          style="margin-left: -7px"
                        />
                      {/each}
                    </div>
                  </TableBodyCell>
                  <TableBodyCell class="p-0 md:table-cell hidden ">
                    <div>
                      <p
                        class="text-right text-[#666C79] text-[12px] leading-4 mb-[6px]"
                      >
                        {product.Seats.title}
                      </p>

                      <Progressbar
                        progress={product.Seats.progress}
                        color={getColor(product.Seats.progress)}
                        size="h-1.5"
                      />
                      <p class="ml-2 text-[#666C79] text-[12px] leading-4 mt-1">
                        {product.Seats.tagline}
                      </p>
                    </div>
                  </TableBodyCell>
                  <TableBodyCell class="p-0">
                    <div class="md:hidden block">
                      <p
                        class="text-right text-[#666C79] text-[12px] leading-4 mb-[6px]"
                      >
                        {product.Seats.title}
                      </p>
                    </div>
                    <p
                      class="text-[#15A033] text-right md:text-left text-base md:px-5"
                    >
                      {product.Sale}
                    </p>
                  </TableBodyCell>
                  <TableBodyCell class="p-0 md:table-cell hidden">
                    <p class="text-[#333B4C] text-xs">{product.Type}</p>
                    <p class="text-[#333B4C] text-xs">Concert</p>
                  </TableBodyCell>
                  <TableBodyCell class="p-0 md:table-cell hidden">
                    <p class="text-[#333B4C] text-xs">{product.Stage}</p>
                  </TableBodyCell>
                  <TableBodyCell class="p-0 md:table-cell hidden">
                    <div class="flex items-center justify-between">
                      {#if product.Status === "On sale"}
                        <div
                          class="bg-[#15A033] bg-opacity-20 rounded-2xl py-1 px-[6px] w-fit"
                        >
                          <div
                            class="flex items-center gap-[2.5px] text-[#15A033] text-xs font-semibold text-center"
                          >
                            <svg
                              width="8"
                              height="8"
                              viewBox="0 0 8 8"
                              fill="none"
                              xmlns="http://www.w3.org/2000/svg"
                            >
                              <circle cx="3.75" cy="4" r="3.5" fill="#15A033" />
                            </svg>
                            <p class="font-semibold">On Sale</p>
                          </div>
                        </div>
                      {/if}
                      {#if product.Status === "Draft"}
                        <div
                          class="bg-[#6C2BD9] bg-opacity-20 rounded-2xl py-1 px-[6px] w-fit"
                        >
                          <div
                            class="flex items-center gap-[2.5px] text-[#6C2BD9] text-xs font-semibold text-center"
                          >
                            <!-- <span class="green-dot"></span> -->
                            <svg
                              width="8"
                              height="8"
                              viewBox="0 0 8 8"
                              fill="none"
                              xmlns="http://www.w3.org/2000/svg"
                            >
                              <circle cx="3.75" cy="4" r="3.5" fill="#6C2BD9" />
                            </svg>
                            <p class="font-semibold">Draft</p>
                          </div>
                        </div>
                      {/if}
                      {#if product.Status === "Scheduled"}
                        <div
                          class="bg-[#FF922E] bg-opacity-20 rounded-2xl py-1 px-[6px] w-fit"
                        >
                          <div
                            class="flex items-center gap-[2.5px] text-[#FF922E] text-xs font-semibold text-center"
                          >
                            <!-- <span class="green-dot"></span> -->
                            <svg
                              width="13"
                              height="12"
                              viewBox="0 0 13 12"
                              fill="none"
                              xmlns="http://www.w3.org/2000/svg"
                            >
                              <circle cx="6.75" cy="6" r="3.5" fill="#FF922E" />
                            </svg>
                            <p class="font-semibold">Scheduled</p>
                          </div>
                        </div>
                      {/if}
                      <div class="relative">
                        <svg
                          on:click={() => toggleDropdown(index)}
                          class="mr-2 cursor-pointer"
                          width="30"
                          height="30"
                          viewBox="0 0 30 30"
                          fill="none"
                          xmlns="http://www.w3.org/2000/svg"
                        >
                          <path
                            d="M11.3998 15C11.3998 15.4774 11.2102 15.9352 10.8726 16.2728C10.535 16.6104 10.0772 16.8 9.5998 16.8C9.12242 16.8 8.66458 16.6104 8.32701 16.2728C7.98945 15.9352 7.7998 15.4774 7.7998 15C7.7998 14.5226 7.98945 14.0648 8.32701 13.7272C8.66458 13.3896 9.12242 13.2 9.5998 13.2C10.0772 13.2 10.535 13.3896 10.8726 13.7272C11.2102 14.0648 11.3998 14.5226 11.3998 15ZM16.7998 15C16.7998 15.4774 16.6102 15.9352 16.2726 16.2728C15.935 16.6104 15.4772 16.8 14.9998 16.8C14.5224 16.8 14.0646 16.6104 13.727 16.2728C13.3894 15.9352 13.1998 15.4774 13.1998 15C13.1998 14.5226 13.3894 14.0648 13.727 13.7272C14.0646 13.3896 14.5224 13.2 14.9998 13.2C15.4772 13.2 15.935 13.3896 16.2726 13.7272C16.6102 14.0648 16.7998 14.5226 16.7998 15ZM20.3998 16.8C20.8772 16.8 21.335 16.6104 21.6726 16.2728C22.0102 15.9352 22.1998 15.4774 22.1998 15C22.1998 14.5226 22.0102 14.0648 21.6726 13.7272C21.335 13.3896 20.8772 13.2 20.3998 13.2C19.9224 13.2 19.4646 13.3896 19.127 13.7272C18.7894 14.0648 18.5998 14.5226 18.5998 15C18.5998 15.4774 18.7894 15.9352 19.127 16.2728C19.4646 16.6104 19.9224 16.8 20.3998 16.8Z"
                            fill="#666C79"
                          />
                        </svg>

                        {#if openDropdownIndex === index}
                          <div
                            class="absolute right-0 mt-2 w-[170px] bg-white rounded-lg shadow-lg z-10 dropdown-content"
                          >
                            <ul class="py-1">
                              <li
                                class="cursor-pointer px-3 py-[15px] hover:bg-gray-100 flex items-center gap-2"
                              >
                                <svg
                                  width="14"
                                  height="14"
                                  viewBox="0 0 16 16"
                                  fill="none"
                                  xmlns="http://www.w3.org/2000/svg"
                                >
                                  <path
                                    d="M12.7025 1.15771C11.8993 0.711794 10.9253 0.726514 10.1356 1.19619C9.88486 1.34531 9.6534 1.56747 9.362 1.87669C9.238 2.00819 9.17606 2.07394 9.17726 2.15505C9.17846 2.23615 9.243 2.30071 9.37213 2.42982L13.633 6.69065C13.7648 6.82251 13.8307 6.88845 13.9133 6.88858C13.9959 6.88878 14.0613 6.82398 14.192 6.69438C14.4725 6.41627 14.6759 6.19079 14.8142 5.94802C15.2699 5.14835 15.284 4.16516 14.8517 3.35242C14.6714 3.01365 14.3679 2.70377 13.9143 2.24075L13.7916 2.11536C13.3396 1.65335 13.0357 1.34269 12.7025 1.15771Z"
                                    fill="#666C79"
                                  />
                                  <path
                                    d="M12.6553 8.1766C12.7934 8.04353 12.8625 7.977 12.8633 7.89306C12.8641 7.80913 12.7963 7.74133 12.6606 7.60566L8.48858 3.43361C8.35031 3.29532 8.28118 3.22617 8.19598 3.22788C8.11078 3.22958 8.04444 3.30144 7.91178 3.44516L2.76118 9.02559C2.01448 9.83439 1.55682 10.3301 1.28892 10.9467C1.02153 11.5621 0.968877 12.2393 0.882783 13.3465L0.882636 13.3484C0.882476 13.3503 0.825643 14.0775 0.834416 14.2349C0.84435 14.4132 0.88681 14.6299 1.05228 14.8177C1.21925 15.0072 1.4303 15.0753 1.60798 15.105C1.76254 15.1308 2.45866 15.1489 2.46006 15.1489C3.72483 15.1823 4.50667 15.2029 5.22565 14.922C5.94361 14.6416 6.51098 14.0949 7.43158 13.2079L12.6553 8.1766Z"
                                    fill="#666C79"
                                  />
                                </svg>
                                <span
                                  class="text-[14px] leading-[14px] text-[#666C79]"
                                  >Edit</span
                                >
                              </li>
                              <li
                                class="cursor-pointer px-3 py-[15px] hover:bg-gray-100 flex items-center gap-2"
                              >
                                <svg
                                  width="16"
                                  height="16"
                                  viewBox="0 0 16 16"
                                  fill="none"
                                  xmlns="http://www.w3.org/2000/svg"
                                >
                                  <path
                                    fill-rule="evenodd"
                                    clip-rule="evenodd"
                                    d="M3.68037 4.4753C4.81746 3.58759 6.28646 2.83331 8.00016 2.83331C9.7139 2.83331 11.1828 3.58759 12.32 4.4753C13.4581 5.36382 14.2993 6.41314 14.7699 7.07298L14.8054 7.12245C14.9742 7.35718 15.1668 7.62518 15.1668 7.99998C15.1668 8.37478 14.9742 8.64278 14.8054 8.87751L14.7699 8.92698C14.2993 9.58685 13.4581 10.6361 12.32 11.5246C11.1828 12.4124 9.7139 13.1666 8.00016 13.1666C6.28646 13.1666 4.81746 12.4124 3.68037 11.5246C2.54225 10.6361 1.701 9.58685 1.23044 8.92698L1.19496 8.87751C1.02619 8.64278 0.833496 8.37478 0.833496 7.99998C0.833496 7.62518 1.02619 7.35718 1.19496 7.12245L1.23044 7.07298C1.701 6.41314 2.54225 5.36382 3.68037 4.4753ZM5.66683 7.99998C5.66683 9.28865 6.7115 10.3333 8.00016 10.3333C9.28883 10.3333 10.3335 9.28865 10.3335 7.99998C10.3335 6.71131 9.28883 5.66665 8.00016 5.66665C6.7115 5.66665 5.66683 6.71131 5.66683 7.99998Z"
                                    fill="#666C79"
                                  />
                                </svg>
                                <span
                                  class="text-[14px] leading-[14px] text-[#666C79]"
                                  >View</span
                                >
                              </li>
                              <li
                                class="cursor-pointer px-3 py-[15px] hover:bg-gray-100 flex items-center gap-2"
                                on:click={() => handleDelete(index)}
                              >
                                <svg
                                  width="16"
                                  height="16"
                                  viewBox="0 0 16 16"
                                  fill="none"
                                  xmlns="http://www.w3.org/2000/svg"
                                >
                                  <path
                                    fill-rule="evenodd"
                                    clip-rule="evenodd"
                                    d="M13.055 10.4376C13.0039 11.2731 12.9633 11.9361 12.8801 12.4656C12.7948 13.0088 12.6583 13.461 12.3851 13.8566C12.1353 14.2186 11.8136 14.524 11.4405 14.7536C11.0327 15.0045 10.5774 15.1142 10.0354 15.1667L5.95159 15.1666C5.409 15.114 4.95315 15.0041 4.54507 14.7527C4.17175 14.5228 3.84996 14.2168 3.60019 13.8542C3.32715 13.458 3.19104 13.005 3.10638 12.4612C3.02383 11.9308 2.98415 11.2669 2.93415 10.4302L2.5 3.16669H13.5L13.055 10.4376ZM6.33333 11.974C6.05719 11.974 5.83333 11.7502 5.83333 11.474V7.47395C5.83333 7.19782 6.05719 6.97395 6.33333 6.97395C6.60947 6.97395 6.83333 7.19782 6.83333 7.47395V11.474C6.83333 11.7502 6.60947 11.974 6.33333 11.974ZM10.1667 7.47395C10.1667 7.19782 9.9428 6.97395 9.66667 6.97395C9.39053 6.97395 9.16667 7.19782 9.16667 7.47395V11.474C9.16667 11.7502 9.39053 11.974 9.66667 11.974C9.9428 11.974 10.1667 11.7502 10.1667 11.474V7.47395Z"
                                    fill="#FF4D4D"
                                  />
                                  <path
                                    fill-rule="evenodd"
                                    clip-rule="evenodd"
                                    d="M8.89836 0.855158C9.2751 0.888851 9.62916 1.00382 9.93323 1.23058C10.1581 1.3983 10.3143 1.60359 10.4478 1.82593C10.5714 2.03196 10.696 2.28884 10.8372 2.58024L11.1217 3.16711H14.0002C14.3684 3.16711 14.6668 3.46559 14.6668 3.83378C14.6668 4.20197 14.3684 4.50044 14.0002 4.50044C10 4.50044 6.00029 4.50044 2.00016 4.50044C1.63198 4.50044 1.3335 4.20197 1.3335 3.83378C1.3335 3.46559 1.63198 3.16711 2.00016 3.16711H4.94L5.1772 2.64675C5.31491 2.34462 5.43618 2.07852 5.558 1.865C5.68941 1.63469 5.84497 1.42156 6.07257 1.24695C6.38038 1.01082 6.74156 0.891105 7.12676 0.856038C7.41676 0.829638 7.7091 0.833271 8.00016 0.833738C8.3407 0.834285 8.64683 0.832658 8.89836 0.855158ZM6.40534 3.16711H9.63996C9.48883 2.85552 9.39216 2.65802 9.30456 2.51211C9.17636 2.29856 9.02276 2.20494 8.77956 2.18319C8.6067 2.16773 8.38143 2.16711 8.02316 2.16711C7.65596 2.16711 7.42483 2.16775 7.24763 2.18388C6.99823 2.20658 6.84276 2.30376 6.7161 2.52575C6.6331 2.67122 6.54274 2.86596 6.40534 3.16711Z"
                                    fill="#FF4D4D"
                                  />
                                </svg>

                                <span
                                  class="text-[14px] leading-[14px] text-[#FF4D4D]"
                                  >Delete</span
                                >
                              </li>
                            </ul>
                          </div>
                        {/if}
                      </div>
                    </div>
                  </TableBodyCell>
                </TableBodyRow>
              {/each}
            </TableBody>
          </Table>
        </div>
      </div>
      <!-- pagination Section -->
      <div
        class="md:flex hidden items-center justify-between mt-2 mx-3 pb-4 bg-transparent"
      >
        <div>
          <p class="text-[#666C79] text-xs">
            Showing <span class="font-bold text-[#08132B]">1-10</span> of
            <span class="font-bold text-[#08132B]">1000</span>
          </p>
        </div>
        <div>
          <div class="flex items-center cursor-pointer border-[1.8px] rounded-lg shadow-sm border-opacity-60 border-[#666C79]">
            <div class="py-[8px]  px-[12px]  ">
              <svg
                width="16"
                height="16"
                viewBox="0 0 16 16"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  d="M10 4C10 4 6.00001 6.94593 6 8C5.99999 9.05413 10 12 10 12"
                  stroke="#666C79"
                  stroke-width="1.5"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                />
              </svg>
            </div>
            <div class="py-[7px] text-[#666C79] px-[12px] border-l-[1.8px] border-r-[1.8px] border-opacity-60 border-[#666C79] ">1</div>
            <div class="py-[7px] text-[#666C79] px-[12px] border-r-[1.8px] border-opacity-60 border-[#666C79]">2</div>
            <div class="py-[7px] text-[#666C79] px-[12px] border-r-[1.8px] border-opacity-60 border-[#666C79]">3</div>
            <div class="py-[7px] text-[#666C79] px-[12px] border-r-[1.8px] border-opacity-60 border-[#666C79]"> ...</div>
            <div class="py-[7px] text-[#666C79] px-[5px] border-r-[1.8px] border-opacity-60 border-[#666C79]">100</div>
            <div class="py-[7px] text-[#666C79] px-[12px] "><svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M6 12C6 12 9.99999 9.05407 10 8C10 6.94587 6 4 6 4" stroke="#666C79" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
              </svg>
              </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</div>

<style>
  .main-container {
    /* background-color: white; */
    width: 100%;
    max-width: 1408px;
    margin: auto;
  }
  .table-main {
    width: 100% !important;
    overflow-x: visible;
  }
  .header-cell {
    padding: 5px 10px;
  }
  /* Styles for dropdown */
  .dropdown-content {
    display: block;
  }
  .dropdown-content ul {
    list-style: none;
    padding: 0;
    margin: 0;
  }
  .dropdown-content li {
    cursor: pointer;
  }
  .dropdown-content li:hover {
    background-color: #f7f7f7;
  }

  @media (min-width: 480px) {
    footer {
      padding: 12px 0;
    }
  }
</style>
