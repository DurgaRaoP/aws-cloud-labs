# EC2 + Security Group Troubleshooting

## Common Issues and Fixes

**Issue: SSH connection timeout**
- Check: Security Group inbound rule for port 22
- Check: Source IP — must allow your IP or 0.0.0.0/0
- Check: Instance is in public subnet with IGW attached
- Check: Route table has 0.0.0.0/0 → Internet Gateway

**Issue: Website not loading (port 80)**
- Check: Security Group inbound rule for port 80
- Check: nginx/httpd service is running → systemctl status nginx
- Check: Service is enabled on boot → systemctl enable nginx

**Commands used:**
- ssh -i key.pem ec2-user@<public-ip>
- systemctl start nginx
- systemctl status nginx
- sudo journalctl -u nginx
