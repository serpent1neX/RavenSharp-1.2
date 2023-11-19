# RavenSharp-1.2
Upgrades and improvements to RavenSharp for better performance and more features

AI Changes  
- Squadmates following their leader will now try to move in a way so they can always have direct line of sight to the squad leader, meaning squads stick closer together in areas with lots of cover.  
- Fixed a bug where the AI sometimes would pick really bad cover points while defending a flag  
- The AI will now prefer to spread out more when picking a cover point.  
- Fixed a bug where the AI would not fire mortar style weapons correctly  
- Improved AI weapon switching, so now they should be way more consistent and not switch out their weapon all the time.  
- Fixed AI crouching/leaning while using cover points.  
- When using slow fire rate weapons like snipers, bots will now wait a little after taking a shot before crouching when behind cover.
- Bots with skill level veteran or higher will now lean while checking corners in close quarters areas.
- Fixed a bug where bots would sometimes walk through geometry when getting a new path while traversing a pathfinding link.
- Fixed multiple bugs where bots would get corrupted paths when walking to capture points after being ragdolled/strafing a target.
- When walking around a corner, bots that lean will now lean more or less depending on their look direction. This should result in smoother looking leans and prevent weird leaning behaviour when aiming backwards, etc.
- Bots will no longer play emote animations while targeting an enemy or reloading.
- Fixed a bug where bots would sometimes look at the ground when approaching the end of their current walking path.
- Bots now go to walkable navmesh nodes inside of the capture range/volume when attacking a flag, this should prevent edge cases where attacking squads think they are attacking a flag when in reality they are standing outside of the capture zone.
- AI can no longer deal friendly fire while using normal projectiles. They can still deal friendly fire by splash damage, however. Previously, AI could deal friendly fire damage when hitting a target 100 meters or futher away
- After firing their weapon, bots will not be able to look around for one second (unless they spot another target to fire at). This fixes an issue where bots would sometimes fire at an enemy, but then look in a completely other direction and continue holding their fire input for a split second, randomly firing projectiles across the level.
- Lots of other small tweaks and improvements to the AI

Ingame Map Editor
- Fixed some map editor props not generating navmesh correctly.
- Fixed skeleton hat missing mesh
- Fixed missing colliders on snowy arch and house stilts

Modding
- Added displayName field for weapons, this is the name that shows up in the new UI.
- Dropped support of the legacy animation component. This component will no longer load from mods. Please use the new animator controller component instead!
- Added component for animated vehicles to drive engine audio from their current speed, this is really useful for cutscenes where the vehicle movement is pre-animated such as the breaching APC in the citadel mission.

Trigger system
- Added ScriptedPathGroups which can be used to manually design paths for bots to follow.
- Added several dozens of logic components that can be used to contorol game flow

Ravenscript
- Added a killCredit property to weapons which is automatically set to whoever equips a weapon, but can be overridden through this value. This value can also be used to set whoever should get the kill from scripted weapons such as automatic turrets, etc.
- Renamed Projectile.source to Projectile.killCredit to match weapon naming convention. Accessing .source will still work, meaning mods using the older name will still work fine.
- Fixed a bug where weapons could not fire projectiles through the Shoot() function unless they were first equipped by an actor. This means that weapons can now be fired via scripts without having to be picked up.
- Exposed functions that can be used to hide individual elements of the new ingame UI. This is great if you're making a custom HUD and only want to replace parts of the vanilla UI.
- Exposed PlayerHud.playerOrderState to RS, which can be used to drive player squad status labels in your custom HUDs
- Added Actor functions to more easily access actor skinned mesh renderers
- Exposed fonts to Ravenscript and DataContainer component
- Various Ravenscript bugfixes
