# Case 001 – EC2 Application Performance Degradation

## Case Title
EC2 Application Performance Degradation Due to High CPU Utilization

## Customer Issue
The customer reported that their EC2-hosted web application was experiencing slow response times and intermittent unavailability during normal usage.

## Severity
Medium  
(Customer-facing performance impact with no data loss)

---

## Environment Details
- Service: Amazon EC2
- Instance Type: t2.micro
- Operating System: Amazon Linux 2
- Application: Apache HTTP Server
- Monitoring: Amazon CloudWatch
- Network: Default VPC with public subnet and Internet Gateway

---

## Investigation Steps

1. Reviewed customer-reported symptoms and confirmed application slowness.
2. Verified EC2 instance state and system status checks (2/2 passed).
3. Analyzed Amazon CloudWatch metrics for CPU utilization and network activity.
4. Logged into the EC2 instance to validate application and system health.
5. Reviewed Apache service status and system logs.

---

## Findings

- EC2 instance was running and reachable.
- No security group or network connectivity issues were identified.
- CloudWatch metrics showed sustained CPU utilization spikes exceeding 80%.
- Apache service was running but performance degraded during CPU saturation.

---

## Root Cause Analysis (RCA)

The EC2 instance was under-provisioned for the application workload.  
High CPU utilization caused resource contention, leading to degraded application performance and intermittent downtime.

---

## Resolution

### Immediate Actions
- Restarted the Apache HTTP service to stabilize application responsiveness.
- Monitored CPU utilization post-restart to confirm temporary improvement.

### Permanent Fix
- Resized the EC2 instance from `t2.micro` to `t3.small` to provide additional CPU capacity.
- Verified application stability after instance resizing.

---

## Preventive Recommendations

- Configure Amazon CloudWatch alarms for CPU utilization thresholds.
- Enable SNS notifications for proactive incident awareness.
- Use Auto Scaling for workloads with variable traffic.
- Perform capacity planning and load testing before production deployment.

---

## Outcome

After instance resizing and monitoring enhancements, the application performance stabilized and no further performance degradation was observed.

---

## Skills Demonstrated
- AWS EC2 troubleshooting
- CloudWatch monitoring and metrics analysis
- Incident response and root cause analysis (RCA)
- Linux system validation
- Customer-focused technical documentation
