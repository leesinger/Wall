if myHero.charName ~= "Vayne" then return end

local ownXRap = 5833
local ownZRap = 5590
local mouseXRap = 6124 --6124
local mouseZRap = 5232 --5232

local ownXInhib = 11922
local ownZInhib = 10006
local mouseXInhib = 12059 --12059
local mouseZInhib = 10395.7 --10395.7

local ownXDrake = 12050
local ownZDrake = 4827
local mouseXDrake = 11514
local mouseZDrake = 4462

local ownXMid = 6958
local ownZMid = 8944
local mouseXMid = 6707.485
local mouseZMid = 8802.744

local distToRapWall
local distToInhibWall
local distToDrakeWall
local distToMidWall

function OnLoad()

test = scriptConfig("WallTumble", "WallTumble")
    
    test:addSubMenu("Enabled", "Enabled")
    test.Enabled:addParam("Go","Go", SCRIPT_PARAM_ONKEYDOWN, false, 32)

end

function OnTick ()

    distToRapWall = GetDistance(myHero, Point(ownXRap, ownZRap))
    distToInhibWall = GetDistance(myHero, Point(ownXInhib, ownZInhib))
    distToDrakeWall = GetDistance(myHero, Point(ownXDrake, ownZDrake))
    distToMidWall = GetDistance(myHero, Point(ownXMid, ownZMid))
    
    local distances = {distToRapWall, distToInhibWall, distToDrakeWall, distToMidWall}
    
    table.sort(distances)

    if test.Enabled.Go and myHero:CanUseSpell(_Q) == READY then

        if distances[1] == distToRapWall then

            if myHero.x <= ownXRap - 5 or myHero.x >= ownXRap + 5 or myHero.z <= ownZRap - 5 or         myHero.z >= ownZRap + 5 then
            player:MoveTo(ownXRap, ownZRap)
            else
            CastSpell(_Q, mouseXRap, mouseZRap)
            end

        end
        if distances[1] == distToInhibWall then
        
            if myHero.x <= ownXInhib - 5 or myHero.x >= ownXInhib + 5 or myHero.z <= ownZInhib - 5 or         myHero.z >= ownZInhib + 5 then
            player:MoveTo(ownXInhib, ownZInhib)
            else
            CastSpell(_Q, mouseXInhib, mouseZInhib)
            end
        
        end
        if distances[1] == distToDrakeWall then

            if myHero.x <= ownXDrake - 5 or myHero.x >= ownXDrake + 5 or myHero.z <= ownZDrake - 5 or         myHero.z >= ownZDrake + 5 then
            player:MoveTo(ownXDrake, ownZDrake)
            else
            CastSpell(_Q, mouseXDrake, mouseZDrake)
            end
        
        end
        if distances[1] == distToMidWall then
        
            if myHero.x <= ownXMid - 5 or myHero.x >= ownXMid + 5 or myHero.z <= ownZMid - 5 or         myHero.z >= ownZMid + 5 then
            player:MoveTo(ownXMid, ownZMid)
            else
            CastSpell(_Q, mouseXMid, mouseZMid)
            end
        
        end

    end

end

function OnDraw ()

if distToRapWall and GetDistance(myHero, distToRapWall) <= 1500 then
    DrawCircle(ownXRap, 0, ownZRap, 100, 0xffffff)
end
if distToInhibWall and GetDistance(myHero, distToInhibWall) <= 1500 then
    DrawCircle(ownXInhib, 0, ownZInhib, 100, 0xffffff)
end
if distToDrakeWall and GetDistance(myHero, distToDrakeWall) <= 1500 then
    DrawCircle(ownXDrake, 0, ownZDrake, 100, 0xffffff)
end
if distToMidWall and GetDistance(myHero, distToMidWall) <= 1500 then
    DrawCircle(ownXMid, 0, ownZMid, 100, 0xffffff)
end

end
