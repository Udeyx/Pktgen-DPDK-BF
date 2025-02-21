Pktgen-DPDK-BF
=====================================================

The Mellanox customized DPDK lacks some struct and function definitions used by Pktgen, and the official DPDK fails to recognize the ports(PF, VF, SF, PF representor, VF representor, SF representor) on BlueField correctly. Besides, some pthread functions used by Pktgen is not defined in DPU OS's pthread.h.

This repo solves above problems by:
1. manually adding and modifying struct definitions(i.e. `rte_ipv6_addr`, `cmdline_ipaddr`) in Pktgen's source code
2. replacing `pthread_set_name_np` with `pthread_setname_np` in `lib/lua/lua_socket.c`