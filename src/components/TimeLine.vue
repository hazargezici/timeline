<template>
  <div class="container">
    <div class="card">
      <div class="waves">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1440 320">
          <path
            fill="#F9C35C"
            fill-opacity="1"
            d="M0,288L48,261.3C96,235,192,181,288,181.3C384,181,480,235,576,261.3C672,288,768,288,864,277.3C960,267,1056,245,1152,245.3C1248,245,1344,267,1392,277.3L1440,288L1440,0L1392,0C1344,0,1248,0,1152,0C1056,0,960,0,864,0C768,0,672,0,576,0C480,0,384,0,288,0C192,0,96,0,48,0L0,0Z"
          ></path>
        </svg>
      </div>
    </div>
    <div class="timeline-container">
      <div class="blur">
        <h3>Updates</h3>
        <p>23 in last 7 hours</p>
      </div>
      <div class="timeline" v-if="timelineData.length > 0">
        <ul class="timeline-list">
          <template v-for="item in timelineData">
            <li class="timeline-item" :key="item">
              <div class="timeline-item-content">
                <b class="timeline-item-date">{{ getDate(item.date) }}</b>
                <p class="timeline-item-desc">{{ item.desc }}</p>
              </div>
            </li>
          </template>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import moment from "moment";
export default {
  name: "TimeLine",
  props: {
    timelineData: {
      type: Array,
      required: true,
    },
  },
  methods: {
    getDate(date) {
      return moment(date).hours() + ":" + moment(date).minutes();
    },
  },
};
</script>

<style scoped lang="scss">
.container {
  & .card {
    background-color: #fb748c;
    height: 160px;
    width: 360px;
    border-radius: 10px;
    svg {
      border-radius: 10px;
    }
  }
  & .timeline-container {
    height: 100%;
    width: 300px;
    margin: auto;
    position: relative;
    top: -100px;
    border-radius: 5px;
    .blur {
      height: 100px;
      background-color: rgba(255, 255, 255, 0.4);
      -webkit-backdrop-filter: blur(5px);
      backdrop-filter: blur(5px);
      border-top-right-radius: 5px;
      border-top-left-radius: 5px;
      line-height: 30px;
      padding-top: 10px;
      padding-left: 30px;
      color: #fff;
    }
    .timeline {
      background-color: #fff;
      border-bottom-right-radius: 5px;
      border-bottom-left-radius: 5px;
      color: black;
      position: relative;
      &:before {
        content: "";
        position: absolute;
        height: 100%;
        width: 2px;
        top: 50%;
        left: 15%;
        transform: translate(-50%, -50%);
        background-color: #a1a0b9;
      }

      &-list {
        list-style: none;
      }

      &-item {
        padding: 25px 5px;
        background-color: #fff;
        box-shadow: 2px 2px 10px 2px rgba(0, 0, 0, 0.2);
        border-radius: 5px;
        width: 70%;
        position: relative;
        top: -30px;
        left: -60px;
        padding-left: 25px;
        &:before {
          content: "";
          position: absolute;
          top: 30px;
          border-radius: 50%;
          background-color: #a1a0b9;
          height: 20px;
          width: 20px;
        }
        transform: translateX(60%);
        &:before {
          left: -31px;
        }

        &:not(:last-child) {
          margin-bottom: 30px;
        }
        &-date {
          font-size: 14px;
        }
        &-desc {
          font-size: 15px;
          overflow: auto;
        }
      }
    }
  }
}
</style>
