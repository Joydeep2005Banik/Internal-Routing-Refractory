# Internal-Routing-Refractory

Introduced a member called 'Ipv4NetworkAddress m_network' for class Ipv4RoutingTableEntry {private:Ipv4RoutingTableEntry(...) in ipv4-routing-table-entry.h .
Introduced its equivalent constructor m_network(...) in ipv4-routing-table-entry.cc .  The aim was to handle both the network address and subnet mask together.

In rip.cc, normalized both the lookup destination and stored route using the subnet mask to ensure canonical (network + mask) comparison. The aim was to avoid mismatches when routes contain non-zero host bits and aligns RIP route lookup with the routing refactoring (MR !2645).
