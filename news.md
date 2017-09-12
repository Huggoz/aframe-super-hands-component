## News

v2.0.0

* Consistent experience across devices: `super-hands` now provides interactivity
  for all levels of VR controls: desktop mouse, mobile touch ("magic window"),
  cardboard button,
  3DOF (GearVR and Daydram), and 6DOF (Vive and Oculus Touch)
  * `progressive-controls` meta-component to automatically setup interactive
    controls on **any** device from desktop to Vive
  * Upgraded `grabbable` reaction component.
    * Now works with pointing and moving at a distance, e.g. with
      3DOF controllers and `laser-controls`, using controller orientation
      and position to move grabbed entities
* Button mapping for reaction components: each reaction component now has
  `startButtons` and `endButtons` schema properties to specify acceptable
  buttons. This allows different entities to react to different buttons.
  [For example](https://wmurphyrd.github.io/aframe-super-hands-component/examples/#locomotion)
  `a-locomotor`'s `grabbable` can be set to respond to different
  buttons than other `grabbable` entities so that
  grabbing entities and locomotion are separate gestures for the user.
* `a-locomotor` now functions independently from colliders;
  removed `add-to-colliders` attribute.
* Performance improvements in `grabbable` and `stretchable`
* Gesture initiation changed to occur only on button press rather than
  button press and collision. Pressing a button in empty space and then
  moving into an object will no long scoop it up in a grab.

v1.1.0

* Compatibility with desktop mouse control via A-Frame `cursor` component
  * Added new schema property `colliderEventProperty` to configure
    where in the `event.details` to look for the collision target
  * Requires some configuration of schema properties, see new example: [Mouse Controls](https://wmurphyrd.github.io/aframe-super-hands-component/examples/#mouse)
* Select examples now have `avatar-replayer` to preview actions without needing
  VR equipment

v1.0.1

* A-Frame v0.6.0 compatibility: fixed issue with camera freezing when using
  `a-locomotor`'s automatic camera config
* Updated documentation and examples with latest versions of `aframe-extras` and
  `aframe-physics-system`.

v1.0.0

* `a-locomotor`: drop-in freedom of motion for WebVR experiences
  with this new primitive
* Maturation of A-Frame style API: Reaction components now need to cancel
  gesture events in order to communicate acceptance of the gesture to `super-hands`.
  This improves state tracking and handling of overlapping/nested
  entities
* Improved Global Event Handlers integration:
    * When overlapping entities create multiple potential targets for GEH
      events, the events fire on all potential targets
    * `click` now functions more like its mouse counterpart, only firing
      if a mouseup occurs after a mousedown and without losing collision
      with the target entity
* Two-handed grabbing: `grabbable` can now process grabs from multiple
  `super-hands` entities. In non-physics interactions, this makes passing
  entities between hands much easier. In physics-based interactions, this
  creates multiple constraints for advanced handling
* `strechable` flexibility: state tracking of hands attempting to
  stretch moved from `super-hands` to `strechable`. This should allow for
  different avatars in a multi-user setting to stretch a single entity
  cooperatively
* Added [machinima testing](https://github.com/wmurphyrd/aframe-machinima-testing)
  for automated testing based on motion-captured user input to improve
  regression detection