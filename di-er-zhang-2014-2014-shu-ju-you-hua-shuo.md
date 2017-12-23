

```
computed: {
    getCnHight: function () {
      return this.collapseData1[0].itemData[0].textarea
    },
    getEnHight: function () {
      return this.collapseData2[0].itemData[0].textarea
    }
  },
  watch: {
    getCnHight: {
      handler: function (val, oldVal) {
        let Cnhight = $('.subjectCoverCn textarea').height()
        let Enhight = $('.subjectCoverEn textarea').height()
        if (Cnhight > Enhight) {
          $('.subjectCoverEn textarea').height(Cnhight)
        } else {
          $('.subjectCoverEn textarea').height(Enhight)
        }
      },
      deep: true
    },
    getEnHight: {
      handler: function (val, oldVal) {
        let Cnhight = $('.subjectCoverCn textarea').height()
        let Enhight = $('.subjectCoverEn textarea').height()
        if (Cnhight > Enhight) {
          Enhight = Cnhight
          console.log(Enhight)
        } else {
          Cnhight = Enhight
          console.log(Enhight)
        }
      },
      deep: true
    }
  },
```



