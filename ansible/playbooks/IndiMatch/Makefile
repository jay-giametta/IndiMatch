SHELL=/bin/bash

INVENTORY ?= './inventory.yml'
PLAYBOOK ?= './site.yml'

# Default target
all:
	ansible-playbook $(PLAYBOOK) -i $(INVENTORY)

common:
	ansible-playbook $(PLAYBOOK) -i $(INVENTORY) -t common