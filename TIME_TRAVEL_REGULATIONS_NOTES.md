import time
from typing import Dict, Any, Optional

class TimelineSystem:
    def __init__(self):
        # Keeps track of travelers to ensure they only transfer once
        self.registered_transfers: Dict[str, bool] = {}

    def run_reality_simulation(self, traveler_id: str, goals: list) -> Dict[str, Any]:
        """
        Sends back a simulation of the reality of their goals 
        so the traveler can see how they feel before committing.
        """
        print(f"\n[SIMULATION] Initializing timeline projection for Traveler {traveler_id}...")
        time.sleep(1)
        
        # Simulate processing the goals against the 2011-2031 historical framework
        simulated_outcome = {
            "target_goals_achieved": True,
            "macro_pillars_preserved": True, # ADA, ACA, Pluto status remain intact
            "butterfly_effect_risk": "Low (Contained within local wrinkle)",
            "emotional_satisfaction_forecast": 0.95 
        }
        
        print(f"[SIMULATION] Projection Complete. Simulated outcome data ready for review.")
        return simulated_outcome

    def scan_memory_and_approve(self, traveler_id: str, user_mind_state: str) -> bool:
        """
        Full memory scanner of their old life to ensure a non-regrettable state
        and confirm if they truly want to proceed or if they changed their mind.
        """
        print(f"\n[SCANNER] Initiating full memory scan for Traveler {traveler_id}...")
        time.sleep(1)
        
        if user_mind_state.lower() == "changed my mind":
            print("[SCANNER] Alert: Traveler has decided against the transfer. Mission aborted safely.")
            return False
            
        print("[SCANNER] Memory analysis: Clear intentionality detected. Non-regrettable state verified.")
        print("[SCANNER] Decision finalized: Traveler is choosing their own future.")
        return True

    def execute_time_machine_transfer(self, traveler_id: str, target_date: str) -> str:
        """
        Executes the permanent one-time transfer, strictly enforcing the regulation.
        """
        # Uncheatable system check: Ensure they have never used the transfer before
        if self.registered_transfers.get(traveler_id, False):
            raise SecurityException(f"CRITICAL ERROR: Traveler {traveler_id} has already executed their single allowed transfer!")
            
        # Hard lock boundaries based on your timeline rules
        if target_date > "2011-08-14":
            return f"Transfer Rejected: Target date cannot pass the August 14th, 2011 structural anchor."

        # Mark the transfer as permanently used in the system
        self.registered_transfers[traveler_id] = True
        
        return f"SUCCESS: Timeline transfer authorized to {target_date}. The future is whatever you make of it."

class SecurityException(Exception):
    pass


# ==========================================
# SYSTEM DEMONSTRATION
# ==========================================
if __name__ == "__main__":
    system = TimelineSystem()
    traveler = "Traveler_01"
    
    # Step 1: Run the simulation to see how they feel about their goals
    my_goals = ["Adjust local wrinkle in 2010", "Keep original spoken words intact"]
    simulation_results = system.run_reality_simulation(traveler, my_goals)
    print(f"Traveler Reviewing Simulation: {simulation_results}")
    
    # Step 2: Traveler evaluates feelings. If satisfied, they proceed to memory scan.
    # Change this to "changed my mind" to test the fallback system!
    current_choice = "proceed with mission" 
    
    if system.scan_memory_and_approve(traveler, current_choice):
        # Step 3: Execute the permanent, uncheatable transfer
        try:
            status = system.execute_time_machine_transfer(traveler, target_date="2011-05-10")
            print(f"\n[SYSTEM LOG] {status}")
            
            # Step 4: Attempting to cheat the system by trying again
            print("\n[SYSTEM LOG] Traveler attempts a secondary exploit transfer...")
            system.execute_time_machine_transfer(traveler, target_date="2011-06-01")
            
        except SecurityException as e:
            print(f"\n[SYSTEM PROTECTION] System locked down successfully: {e}")
