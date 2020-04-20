1.  DelegatingFilterProxy：filter的代理，通过spring容器管理filter的生命周期
2.  FilterChain：在一个web app里可以注册多个filter，web容器将多个filter组合成一个FilterChain
3.  HttpSecurity：
    1.  addFilterBefore(Filter filter,CLass<? extends Filter> beforeFilter) 在beforeFilter之前添加filter
    2.  addFilterAfter(Filter filter,Class<? extends Filter> afterFilter) 在 afterFilter 之后添加filter
    3.  addFilterAt(Filter filter, Class<? extends Filter> atFilter) 在atFilter相同的位置添加FIlter ，此Filter 不覆盖Filter