
# Active-Active vs Active-Passive

In this topic I am assuming that you already know of this topic. For more information on Active-Active and
Active-Passive, refer to some below reads.

- https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/dns-failover-types.html
- https://www.jscape.com/blog/active-active-vs-active-passive-high-availability-cluster

Below you can refer to my personal guide when to use active-active vs active passive. You may find that some points
across the two replication methods are important in your case. Find which ideas are most important and choose 
from there.

---



### When to Choose Active-Active

 - Keeping the cost of an application is low (fewer pods needed)
 - The application is scaling fast. You find that you need to add more replicas frequently (daily)
   - In this case if Pods or replicas fail there should be others to take some burden with a load-balancer in place.

### When to Choose Active-Passive

 - When having a resilient application is important for your business needs
 - Your application regularly fails
   - This is a short term fix. You should look at Principles on Failure. 
 - You are building a small application that'll never be used in high rates.
   - Best to ensure more resiliency