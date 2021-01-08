 (function(global) {
     function utilsSDK() {
         var that = this;
         this.base_domain = 'http://app.ytjmall.com';
        //   this.base_domain = 'http://192.168.102.24';
         this.base_image = "http://static.ytjmall.com";
         this.init = function() {
                 api.addEventListener({
                     name: 'online'
                 }, function(ret, err) {
                     api.toast({
                         msg: '已连接网络',
                         duration: 2000,
                         location: 'bottom'
                     });
                 });
             },
             //公共请求方法
             //  6a71e69d9b22b09ffdd10e2440834acd
             this.request = function(params) {
                 params.url = params.url || '';
                 params.query = params.query || {};
                 params.success = params.success || function() {};
                 params.error = params.error || function() {};
                 params.query.token = $api.getStorage('token') != 'undefiled' ? $api.getStorage('token') : '';
                 params.query.auth = $api.getStorage('auth') != 'undefiled' ? $api.getStorage('auth') : '';
                 api.ajax({
                     url: params.url,
                     method: 'post',
                     dataType: params.dataType || 'json',
                     data: {
                         values: params.query
                     }
                 }, function(ret, err) {
                     if (ret) {
                         console.log(params.name + "请求成功");
                         params.success(ret, true);
                         if (ret.statusCode == 5) {
                             api.toast({
                                 msg: '登录已过期,请重新登录',
                                 duration: 2000,
                                 location: 'bottom'
                             });

                         }
                     } else {
                         params.error(params.name + err + "请求错误", false);
                     }
                 });
             },
             //公共请求方法,不许要验证
             this.request_ = function(params) {
                 params.url = params.url || '';
                 params.query = params.query || {};
                 params.success = params.success || function() {};
                 params.error = params.error || function() {};
                 api.ajax({
                     url: params.url,
                     method: 'post',
                     dataType: 'json',
                     data: {
                         values: params.query
                     }
                 }, function(ret, err) {
                     if (ret) {
                         console.log(params.name + "请求成功");
                         params.success(ret, true);
                     } else {
                         params.error(params.name + "请求错误" + JSON.stringify(err), false);
                     }
                 });
             },
             this.openWin = function(name, url, pageParam, bounces) {
                 bounces = bounces == 1 ? false : true;
                 api.openWin({
                     name: name,
                     url: url,
                     showProgress: true,
                     reload: true,
                     vScrollBarEnabled: true,
                     hScrollBarEnabled: false,
                     bounces: bounces,
                     pageParam: pageParam
                 });
             },
             this.closeWin = function() {
                 api.closeWin();
             }
     }
     global.utils = new utilsSDK();

 })(window);
