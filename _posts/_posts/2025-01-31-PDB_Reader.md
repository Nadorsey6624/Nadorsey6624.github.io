

[Uploading Ne{
 "cells": [
  {
   "cell_type": "code",
   "execution_count": 1,
   "id": "63bc3af1-28ba-454b-b9e1-06f123566f7a",
   "metadata": {},
   "outputs": [],
   "source": [
    "#GOAL MAKE A LINE OF CODE TO COUNT THE NUMBER OF CHAINS IN PDB FILE"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 14,
   "id": "91ab14b0-db88-47b6-8197-fff1ce0ad6f2",
   "metadata": {},
   "outputs": [],
   "source": [
    "import os \n",
    "import sys\n",
    "#sys.path.append('/home/nadorsey/.local/lib/python3.9/site-packages')\n",
    "from tabulate import tabulate\n",
    "import Bio \n",
    "from Bio.PDB import *\n",
    "from Bio.PDB.MMCIFParser import MMCIFParser \n",
    "from Bio.PDB.MMCIF2Dict import MMCIF2Dict\n",
    "from Bio import PDB\n",
    "import numpy as np \n",
    "import pandas as pd \n",
    "import matplotlib.pyplot as plt "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 21,
   "id": "99d1da17-87cd-4ced-a93f-6865d052cf73",
   "metadata": {},
   "outputs": [
    {
     "name": "stdin",
     "output_type": "stream",
     "text": [
      "Please input your PDB id. Ex: 4jpp \n",
      " 1ec1\n"
     ]
    },
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Structure exists: '/home/nadorsey/jupyter_notebook/pdfiles/1ec1.cif' \n",
      "/home/nadorsey/jupyter_notebook/pdfiles/1ec1.cif\n",
      "1ec1\n",
      "Structure exists: './pdb1ec1.ent' \n",
      "Number of chains in 1ec1: 2\n"
     ]
    },
    {
     "name": "stderr",
     "output_type": "stream",
     "text": [
      "WARNING: The default download format has changed from PDB to PDBx/mmCif\n"
     ]
    }
   ],
   "source": [
    "yourPDB = input('Please input your PDB id. Ex: 4jpp \\n')\n",
    "pdbfile = PDBList()\n",
    "pdbf = pdbfile.retrieve_pdb_file(yourPDB, pdir = \"/home/nadorsey/jupyter_notebook/pdfiles/\")\n",
    "print(pdbf)\n",
    "print(yourPDB)\n",
    "\n",
    "pdbl = PDB.PDBList()\n",
    "pdb_path = pdbl.retrieve_pdb_file(yourPDB, pdir=\".\", file_format=\"pdb\")\n",
    "\n",
    "\n",
    "parser = PDB.PDBParser(QUIET=True)\n",
    "structure = parser.get_structure(yourPDB, pdb_path)\n",
    "num_chains = len({chain.id for chain in structure.get_chains()})\n",
    "\n",
    "print(f\"Number of chains in {yourPDB}: {num_chains}\")\n",
    "\n",
    "\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "934f9d10-4d76-4714-ac4e-01d80313f70f",
   "metadata": {
    "scrolled": true
   },
   "outputs": [],
   "source": [
    "test1=pdbf.split(\".\")[1]\n",
    "print(test1)\n",
    "pdb_id = pdbf.split(\".\")[0]\n",
    "print(pdb_id)\n",
    "\n",
    "if test1 == \"cif\":\n",
    "    parser = MMCIFParser()\n",
    "    structure = parser.get_structure(pdb_id, pdbf)\n",
    "    print(type(structure))\n",
    "    for model in structure:\n",
    "        print(model)\n",
    "        for residue in chain:\n",
    "            print(residue)\n",
    "\n",
    "elif test1 == \"pdb\":\n",
    "    parser = PDBParser(PERMISSIVE = TRUE, QUIET = False)\n",
    "    structure = parser.get_structure(pdb_id,pdbf)\n",
    "    print(type(structure))\n",
    "    for model in structure:\n",
    "        print(model)\n",
    "        for residue in chain:\n",
    "            print(residue)\n",
    "elif test1 == \"mmtf\":\n",
    "    parser = MMTFParser()\n",
    "    structure = MMTFParser.get_structure(\"PDB/pdbf\")\n",
    "\n",
    "elif test1 == \"ent\":\n",
    "    pqr_parser = PDBParser(PERMISSIVE=1, is_pqr=True)\n",
    "    structure = parser.get_structure(pdb_id,pdbf, is_pqr=True)\n",
    "\n",
    "\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "28f2dd96-cc98-4983-8c7a-a72ed1aa7219",
   "metadata": {},
   "outputs": [],
   "source": [
    "    "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "b898bac4-9f21-4437-8f92-3d853b4a2767",
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3 (ipykernel)",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.9.13"
  },
  "widgets": {
   "application/vnd.jupyter.widget-state+json": {
    "state": {},
    "version_major": 2,
    "version_minor": 0
   }
  }
 },
 "nbformat": 4,
 "nbformat_minor": 5
}
wPRJ-Copy1.ipynb…]()
