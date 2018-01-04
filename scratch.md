#vue2.0+Element

##关于初始化遇到的一些小问题

####form表单的初始化
    <script>
        import fetchff from 'src/api'
        export default {
               data: function () {
                     //这里就是初始的值的定义（不多说明）
               },
               created() {
                 this.getData();
               },
               methods: {
                  getData() {
                     let self = this; //注意let的用法这里声明self来区别this的指向
                     if (typeof(self.$route.params.id) != "undefined") {
                         self.stopId = self.$route.params.id;
                         fetchff(self.stopId).then(response => {    // fetchff相对应的一个接口
                             self.form = response;
               //上面是讲返回的值按照对应的key自动填入form表单里面，所以在表单的取名时一定要和返回的值匹配
               //之前由于没有匹配上一直出现初始化一闪而过的现象，即使在return里赋值过，但是在response里没有对应的key造成相应字段为空
                         }).catch(err => {
                             console.log(err)
                         });
                     }
                 },
               }
        }
    </script>
####[个人git地址](https://github.com/cozk)