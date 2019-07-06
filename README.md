## js-utils

js 简单工具

```js
/**
 * @author tellsea
 * @version v0.0.1
 * @description javascript 常用工具类
 * @date: 2019/7/5 15:30
 */

var validator = {

    /**
     * 非空验证
     *
     * @param val
     * @returns {boolean}
     */
    isEmpty(val) {
        if (val == undefined || val == null || val == '') {
            return true;
        } else {
            return false;
        }
    },

    /**
     * 邮箱验证
     *
     * @param val
     * @returns {boolean}
     */
    isEmail(val) {
        var reg = /^([a-zA-Z]|[0-9])(\w|\-)+@[a-zA-Z0-9]+\.([a-zA-Z]{2,4})$/;
        return reg.test(val);
    },

    /**
     * 身份证号码验证
     *
     * @param val
     * @returns {boolean}
     * 身份证正则表达式(15位):isIDCard1=/^[1-9]\d{7}((0\d)|(1[0-2]))(([0|1|2]\d)|3[0-1])\d{3}$/;
     * 身份证正则表达式(18位):isIDCard2=/^[1-9]\d{5}[1-9]\d{3}((0\d)|(1[0-2]))(([0|1|2]\d)|3[0-1])\d{4}$/;
     */
    isCard(val) {
        var reg = /(^\d{15}$)|(^\d{18}$)|(^\d{17}(\d|X|x)$)/;
        return reg.test(val);
    },

    /**
     * 手机号码
     *
     * @param val
     * @returns {boolean}
     */
    isPhone(val) {
        var reg = /^[1][3,4,5,6,7,8,9][0-9]{9}$/;
        return reg.test(val);
    },

    /**
     * 固定电话
     *
     * @param val
     * @returns {boolean}
     */
    isLandline(val) {
        var reg = /^(\(\d{3,4}\)|\d{3,4}-|\s)?\d{7,14}$/;
        return reg.test(val);
    },

    /**
     * 手机号码或者固定电话
     *
     * @param val
     * @returns {boolean}
     */
    isPhoneOrLandline(val) {
        var reg = /^((0\d{2,3}-\d{7,8})|(1[3456789]\d{9}))$/;
        return reg.test(val);
    },

    /**
     * 邮编
     *
     * @param val
     * @returns {boolean}
     */
    isPostalcode(val) {
        var reg = /^[1-9][0-9]{5}$/;
        return reg.test(val);
    },

    /**
     * 银行卡号，15,16,19位
     *
     * @param val
     * @returns {boolean}
     */
    isBank(val) {
        var reg = /^([1-9]{1})(\d{14}|\d{18}|\d{15})$/;
        return reg.test(val);
    },
};

var array = {
    /**
     * 删除数组中的元素
     *
     * @param array 数组
     * @param del 需要删除的元素
     * 1、删除数组中的某个元素，首先需要确定需要获得删除元素的索引值
     * 2、找到相对应的索引值后，根据索引值删除数组中该元素对应的值
     */
    removeElement(arr, del) {
        Array.prototype.indexOf = function (val) {
            for (var i = 0; i < this.length; i++) {
                if (this[i] == val) {
                    return i;
                }
            }
            return -1;
        };
        Array.prototype.remove = function (val) {
            var index = this.indexOf(val);
            if (index > -1) {
                this.splice(index, 1);
            }
        };
        arr.remove(del);
    },

    /**
     * 根据一个父数组删除子数组相对应的元素
     *
     * @param arr1 父数组
     * @param arr2 子数组
     * @returns {*}
     */
    removePoint(arr1, arr2) {
        for (let i = 0; i < arr2.length; i++) {
            for (let j = 0; j < arr1.length; j++) {
                if (arr2[i] == arr1[j]) {
                    let index = arr1.indexOf(arr1[j]);
                    arr1.splice(index, 1);
                }
            }
        }
        return arr1;
    }
};
```
