# railgun-relayer-playbook
Automatically install a Railgun Relayer using Ansible.

## Requirements
You'll need a machine (virtual or physical) with roughly the same hardware requirements as the Railgun Relayer. See the [relayer](https://github.com/Railgun-Community/relayer) repository for details.

You'll also need a machine with Ansible installed. This can be a computer you trust, or it can be the machine you're installing the Relayer on - either is fine.

## Getting started
* Check out a copy of this repository.

```
git clone https://github.com/Zorlin/railgun-relayer-playbook.git
cd railgun-relayer-playbook
```

* Generate an SSH key if you don't already have one.

`ssh-keygen`

* Copy your SSH key to the relayer you want to manage (replace example-host with your server's address).

`ssh-copy-id example-host`

* Edit the `inventory` file. Place your relayer in the [railgun_relayer] group. If you are running Ansible on the same machine you wish to install a relayer on, you can leave the inventory file as-is.

Here's an example:
```
[railgun_relayer]
railgun.windowpa.in
```

* Install the Ansible Galaxy roles and collections needed to run the playbook:

`ansible-galaxy install -r roles/requirements.yml`

* Now you're ready to rock! Run Ansible, fill in the details it asks for and watch as it sets up your relayer.

`ansible-playbook site.yml --ask-become-pass`

* You should see a message like this once Ansible finishes, indicating a successful run:

```
TASK [Success!] **********************************************************************************************
ok: [example.com] => {
    "msg": [
        "Railgun Relayer has been successfully deployed.",
        "Let us know if it worked, and feel free to reach out if you need help. Enjoy!"
    ]
}
```

## Credits
railgun-relayer-playbook was created in 2022 by [Benjamin Arntzen](https://github.com/Zorlin). Example configuration and code by the Railgun team.
