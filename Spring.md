# bean的声明周期
```
public void refresh() throws BeansException, IllegalStateException {
        synchronized(this.startupShutdownMonitor) {
            this.prepareRefresh();//准备刷新(准备工作)
            ConfigurableListableBeanFactory beanFactory = this.obtainFreshBeanFactory();//获得一个新鲜的工厂
            this.prepareBeanFactory(beanFactory);//给beanFactory设置属性值

            try {
                this.postProcessBeanFactory(beanFactory);//返回的为空  所以不重要
                this.invokeBeanFactoryPostProcessors(beanFactory);//Instantiate(实例化) and invoke（调用） all registered  BeanFactoryPostProcessor beans
               
                //下面五个方法都是实例化前的初始工作
		this.registerBeanPostProcessors(beanFactory);//Instantiate(实例化) and register all BeanPostProcessod beans   注册了但是并没去执行
                this.initMessageSource();//做国际化处理 
                this.initApplicationEventMulticaster();//初始化应用程序事件的多播器，方便后续用来发布监听事件
                this.onRefresh();//返回的为空  所以不重要
                this.registerListeners();//注册监听器
                
                this.finishBeanFactoryInitialization(beanFactory); //Instantiate all remaining(non-lazy-init) singletons 实例化所有的剩下的非懒加载的单例对象
                this.finishRefresh();
            } catch (BeansException var9) {
                if (this.logger.isWarnEnabled()) {
                    this.logger.warn("Exception encountered during context initialization - cancelling refresh attempt: " + var9);
                }
                this.destroyBeans();
                this.cancelRefresh(var9);
                throw var9;
            } finally {
                this.resetCommonCaches();
            }

        }
    }
}
```
## prepareRefresh准备工作<br>
```
 protected void prepareRefresh() {
        this.startupDate = System.currentTimeMillis();//设置启动时间
        this.closed.set(false); //设置容器关闭
        this.active.set(true);//设置容器活跃
        if (this.logger.isDebugEnabled()) {
            if (this.logger.isTraceEnabled()) {
                this.logger.trace("Refreshing " + this);
            } else {
                this.logger.debug("Refreshing " + this.getDisplayName());
            }
        }
        this.initPropertySources();//初始化一些资属性源
        this.getEnvironment().validateRequiredProperties();//获取环境对象 并且验证属性值
        if (this.earlyApplicationListeners == null) {
            this.earlyApplicationListeners = new LinkedHashSet(this.applicationListeners);
        } else {
            this.applicationListeners.clear();
            this.applicationListeners.addAll(this.earlyApplicationListeners);
        }
        
        this.earlyApplicationEvents = new LinkedHashSet();//创建集合
    }
```
## prepareBeanFactory创建工厂<br>
```
protected ConfigurableListableBeanFactory obtainFreshBeanFactory() {
                refreshBeanFactory();
		return getBeanFactory();
	}
```
### 在创建工厂的同时加载了配置文件
```
	protected final void refreshBeanFactory() throws BeansException {
		if (hasBeanFactory()) {
			destroyBeans();//判断有没有工厂  有的话销毁
			closeBeanFactory();
		}
		try {
			DefaultListableBeanFactory beanFactory = createBeanFactory();//*创建工厂     工厂名字DefaultListableBeanFactory
			beanFactory.setSerializationId(getId());//设置属性值
			customizeBeanFactory(beanFactory);//设置属性值
			loadBeanDefinitions(beanFactory);//*加载配置文件 xml
			this.beanFactory = beanFactory;
		}
		catch (IOException ex) {
			throw new ApplicationContextException("I/O error parsing bean definition source for " + getDisplayName(), ex);
		}
	}
```
## prepareBeanFactory创建工厂<br>
```
```

