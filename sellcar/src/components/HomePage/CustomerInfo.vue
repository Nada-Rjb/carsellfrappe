<template>
    <section class="hero flow section" data-padding="compact">
      <div class="wrapper" id="main">
        <img class="customer-img" :src="customerImage" alt="Customer Image" />
        <div class="infomatin">
          <div>
            <h3>اسم العميل</h3>
          </div>
          <div class="info">
            <p>مسار الحركه</p>
            <img class="map-icon" src="../../assets/imges/map.png" alt="Map" />
          </div>
        </div>
      </div>
    </section>
  </template>
  
  <script>
  export default {
    data() {
      return {
        customerImage: "../../assets/imges/elfateh.jpg", // Default Image
      };
    },
  };
  </script>
  
  <style lang="scss" scoped>
  .section {
    --pading: 0.1rem;
    padding-block: var(--pading);
  }
  .wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
  
  .customer-img {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    aspect-ratio: 16 / 9;
    object-fit: cover; /* Better scaling */
    background-color: #eee;
    border-radius: 10px;
  }
  
  .infomatin {
    display: flex;
    flex-direction: column;
    width: 90%;
    padding: 0.5rem;
    gap: 0.1rem;
  }
  .hero {
    align-items: center;
    text-align: start;
  }
  
  .info {
    width: 100%;
    display: flex;
    flex-direction: row;
    gap: 0.5rem;
    justify-content: space-between;
    align-items: center;
    p {
      color: #757575;
    }
  }
  
  .map-icon {
    width: 50px;
    height: 50px;
    align-self: center; /* Keep it aligned */
  }
  </style>