# COLOQUE O SCRIPT EM 'STARTERPLAYERSCRIPTS'
# é um script local





local Players = game:GetService("Players")
 
-- Get the player's character and humanoid
local player = Players.LocalPlayer
player.CharacterAdded:Connect(function(character)
    local humanoid = character:WaitForChild("Humanoid")
    
    -- Animation setup
    local runAnimation = Instance.new("Animation")
    runAnimation.AnimationId = "rbxassetid://48885239" -- Replace with your animation ID
    
    local runAnimationTrack = humanoid:LoadAnimation(runAnimation)
    
    -- Play the custom run animation
    humanoid.Running:Connect(function(speed)
        if speed > 0 then
            if not runAnimationTrack.IsPlaying then
                runAnimationTrack:Play()
            end
        else
            if runAnimationTrack.IsPlaying then
                runAnimationTrack:Stop()
            end
        end
    end)
end)
