## How is it works

- Target host must be provisioned on the provider with a pre-shared SSH key configured into it.
- The private SSH key will be accessible to Ansible.
- Ansible task:
  - Update the target host packages.
  - Read the clients variable(A list client names and their emails).
  - Use the open-vpn install script to generate a ovpn-client per client in a certain directory.
  - Use the pre-shared SMTP token to send ovpn-clients to associated client via email.
  - Append the `duplicate-cn` directive to the openvpn server configuration file(/etc/openvpn/server/server.conf).
  - Restart the open vpn server service(openvpn-server@server.service), and make sure it starts on server boot.
