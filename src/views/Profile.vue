<template>
  <div id="profile_container">
    <img id="profile_img" src="../assets/logo.png" alt="" />
    <h2>副島優希</h2>
    <div id="profile_description">
      <p class="profile_text">
        {{ Birthdate.year }}年{{ Birthdate.month }}月{{ Birthdate.day }}日産まれ
        {{ Age }}歳
      </p>
      <p class="profile_text">{{ Position }}</p>
      <div id="profile_intro" class="profile_text">
        <p>自己紹介文</p>
      </div>
    </div>
    <!-- <div id="socials">
      <a href="SNSリンク" class="social_icon">
        <img src="../assets/SNS1_logo.svg" />
      </a>
      <a href="SNSリンク" class="social_icon">
        <img src="../assets/SNS2_logo.png" />
      </a>
    </div> -->
  </div>
</template>
<script>
export default {
  data() {
    return {
      Age: 0,
      Birthdate: {
        day: 6,
        month: 5,
        year: 2001,
      },
      Position: "",
    };
  },
  created() {
    this.InitAge();
    this.InitPosition();
  },
  methods: {
    InitAge() {
      let birthdate = new Date(
        this.Birthdate.year,
        this.Birthdate.month - 1,
        this.Birthdate.day
      );
      let today = new Date();
      let age = today.getFullYear() - birthdate.getFullYear();
      if (
        today.getMonth() < birthdate.getMonth() ||
        (today.getMonth() === birthdate.getMonth() &&
          today.getDate() < birthdate.getDate())
      ) {
        age--;
      }
      this.Age = age;
    },
    InitPosition() {
      let grade = this.Age - 21;
      if (grade < 1) {
        this.Position = "大学" + (4 - grade) + "年生";
      } else {
        this.Position = "社会人" + grade + "年目";
      }
    },
  },
};
</script>
<style lang="scss" scoped>
#profile_container {
  width: 100%;
  height: auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  #profile_img {
    width: 300px;
    height: 300px;
    border-radius: 100px;
    margin: 15px;
  }

  @media screen and (max-width: 400px) {
    #profile_img {
      width: 200px;
      height: 200px;
      border-radius: 75px;
    }
  }

  #profile_description {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;

    .profile_text {
      padding: 10px;
      font-size: 19px;
    }

    @media screen and (max-width: 400px) {
      .profile_text {
        padding: 10px 25px;
      }
    }
  }

  #socials {
    width: 100%;
    height: auto;
    margin-bottom: 20px;
    display: flex;
    flex-wrap: wrap;
    flex-direction: row;
    align-items: center;
    justify-content: center;

    .social_icon {
      width: 100px;
      height: 100px;
      border-radius: 100px;
      margin: 10px;

      img {
        width: 100%;
        height: 100%;
        border-radius: 100px;
        transition: 0.3s;

        &:hover {
          box-shadow: 0px 2px 10px -2px #777777;
        }
      }
    }
  }
}
</style>
