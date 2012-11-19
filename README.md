springframework-lua-view
========================

Emits Lua output in spring 3 framework.

The MappingLuaView can be used in the ContentNegotiatingViewResolverBean to quickly support Lua output. It's based on MappingJacksonView.

In your Spring config xmls... renderedAttributes set is used for filtering the model
```
<!-- Rendered Attributes -->
<util:set id="renderedAttributes">
  <value>response</value> <!-- eg. only syndicate the response attribute of the model -->
</util:set>

<!-- Content Negotiation -->
<bean class="org.springframework.web.servlet.view.ContentNegotiatingViewResolver" p:order="0">
  	<property name="mediaTypes">
      	<map>
      		.
      		.
      		.
          	<entry key="lua" value="application/x-lua" />
      	</map>
  	</property>

	.
	.
	.
  	
  	<property name="defaultViews">
      	<list>
      		.
      		.
      		.
          	<!-- Lua view -->
          	<bean class="name.uddhav.springframework.web.servlet.view.MappingLuaView" p:contentType="application/x-lua" p:renderedAttributes-ref="renderedAttributes" />
        </list>
  	</property>
</bean>  
```