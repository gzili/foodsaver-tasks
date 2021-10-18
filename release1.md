# Tasks for the last week until release

## Backend functionality

- [x] Proper offer creation (DTO, validation, reference to current user, creation of `Food` object and proper reference to it) \[Edvinas]
- [ ] File upload (needed for creation of offers). Probably needs adjustments in controller to accept `multipart/form-data` in request \[Gustas]
- [x] Route that returns all offers for the currently logged in user
- [x] Validation of all registration fields
- [x] Validation of all login fields

## Compliance with requirements

- [x] Standard property
- [x] Named arguments (OffersController, Create())
- [x] Optional arguments (FileService, SerliazeJson())
- [ ] Extension method (siūlau šito nedaryt)
- [x] Widening type casts (OffersController, Create())
- [ ] Narrowing type casts (nesugalvoju kur šitą panaudot, nes mes neturim normalių base klasių...)
- [x] Standard interfaces (IEquatable already implemented, IComparable for Offer)
