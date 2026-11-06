import math
def dew_point(T,RH):
    gamma=math.log(RH/100) + (17.62*T)/(243.12+T)
    return 243.12*gamma/(17.62-gamma)
def frost_point(T,RH):
    gamma = math.log(RH/100) + (17.62*T)/(243.12+T)
    return 272.62*gamma/(22.46-gamma)
T= float(input("Input Temperature value in°C:"))
RH = float(input("Input Relative Humidity in %:"))

td=dew_point(T,RH)
if(td > 0):
    print("Dew point is at ",round(td, 1),("°C"))
else:
    tf = frost_point(T, RH)
    print("Frost point is at", round(tf, 1), "°C")

def surface_temp(T_amb, T_in, t, k, h_out, h_in):
    R_total=1/h_out+t/k+1/h_in
    q=(T_amb-T_in)/R_total
    return T_amb-q/h_out

T_in  = 4        # fridge inside temperature, °C
k     = 0.022    # PU foam insulation, W/m·K
h_out = 8        # outside heat transfer coefficient, W/m²·K
h_in  = 5        # inside heat transfer coefficient, W/m²·K

wall   = surface_temp(T, T_in, 0.050, k, h_out, h_in)   # 50 mm insulation
gasket = surface_temp(T, T_in, 0.005, k, h_out, h_in)   # 5 mm near the door seal

for name , Ts in [("Wall", wall),("Gasket area",gasket)]:
    margin = Ts-td
    if margin > 0:
        print(name,"surface",round(Ts, 1), "°C -> dry(",round(margin, 1), "K above dew point)")
    else:
        print(name, "surfaace:", round(Ts, 1),"°C -> CONDENSATION RISK (", round(-margin, 1 ),"K belowdew point)")
