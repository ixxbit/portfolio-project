# Autoscaling

[\#Kubernetes](https://www.linkedin.com/feed/hashtag/?keywords=kubernetes&highlightedUpdateUrns=urn%3Ali%3Aactivity%3A6639770894103302144) autoscaling.   
How does it work?   
  
  
Scaling is an essential operational practice that used to be done manually for a long time concerning applications, with the introduction of tools like Kubernetes, the things have changed dramatically in the software industry.  
  
In the context of the Kubernetes cluster, there are typically two things you would like to scale as a user, Pods, and Nodes.  
  
There are three types of scaling:   
&gt; HorizontalPodAutoscaler  
&gt; VerticalPodAutoscaler, and   
&gt; Cluster Autoscaler.   
  
With these techniques, Kubernetes can take intelligent scaling decisions automatically.  
  
HorizontalPodAutoscaler refers to increasing the number of Pods serving the application, in response to the present computational needs.   
  
VerticalPodAutoscaler involves expanding the resources of the Pods.  
  
Cluster Autoscaler \(CA\) scales your node clusters based on the number of pending pods. It checks to see whether there are any pending pods and increases the size of the cluster so that these pods can be created.   
  
Mastering autoscaling needs some patience and persistent efforts to see which technique suits your app's needs by doing trial and error.   
Continuous learning and experimentation is the key:\)  
  
Which autoscaling technique do you prefer?![Kubernetes autoscaling ](https://media-exp1.licdn.com/dms/image/C4E22AQG6st0zWQqTpQ/feedshare-shrink_800/0?e=1586995200&v=beta&t=24baoIxe1crAbDdHETaU5AT1NKeXyKx53GN7WFdQhtQ)

