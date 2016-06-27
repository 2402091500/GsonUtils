```java
public class GsonUtils {
    private static final String TAG = "GsonUtils";

    private static Gson gson = new Gson();

    /**
     *
     * @param json Json字符串eg:{"result":2,"message":"\u5446\u840c\u4e86\u4e00\u4e0b\uff0c\u8bf7\u7a0d\u540e\u91cd\u8bd5~","data":{}}
     * @param cls 实体类
     * @param <T> 实体类类型
     * @return 含有内容的实体类对象
     */
    public static <T> T getObject(String json, Class<T> cls) {
        T t = null;
        try {
            ULog.i(TAG, "getObject", "json：" + json);
            t = gson.fromJson(json, cls);
        } catch (Exception e) {
            ULog.e(e);
            return null;
        }
        return t;
    }

      /**
     *
     * @param fields 实体类对象
     * @return 含有内容的实体类对象对应的Json字符串eg:{"page":"1","uids":"5733","sessionToken":"lrqbmZSFvCkapcrIvFAHmxjv"}
     */
    public static String getClass2Json(BaseFields fields) {
        ULog.i(TAG, "getClass2Json", gson.toJson(fields));
        return gson.toJson(fields);
    }

    /**
     *
     * @param fields 实体类对象
     * @return 含有内容的实体类对象对应的Json字符串eg:{"page":"1","uids":"5733","sessionToken":"lrqbmZSFvCkapcrIvFAHmxjv"}
     */
    public static String getClass2Json(Login_Phone_Request fields) {
        ULog.i(TAG, "getClass2Json", gson.toJson(fields));
        return gson.toJson(fields);
    }

    public static String userBasic2Json(UserInfo.BasicInfo basic) {
        return gson.toJson(basic);
    }
    public static String userExt2Json(UserInfo.ExtInfo ext) {
        return gson.toJson(ext);
    }

    public static <T> ArrayList<T> jsonArrayToArrayList(JsonArray jsonArray, Class<T> cls) {
        if (null == jsonArray || 0 == jsonArray.size()) {
            return new ArrayList<>();
        }
        int length = jsonArray.size();
        ArrayList<T> arrayList = new ArrayList<>(length);
        for (int i = 0; i < length; ++i) {
            T t = gson.fromJson(jsonArray.get(i), cls);
            arrayList.add(t);
        }
        return arrayList;
    }
}
```