# Tasks for the last week until release

## Backend functionality

- [ ] Proper offer creation (DTO, validation, reference to current user, creation of `Food` object and proper reference to it) \[Edvinas]
- [ ] File upload (needed for creation of offers). Probably needs adjustments in controller to accept `multipart/form-data` in request \[Gustas]
- [ ] Route that returns all offers for the currently logged in user
- [ ] Validation of all registration fields
- [ ] Validation of all login fields

## Compliance with requirements

- [ ] Standard property
- [x] Named arguments (OffersController, Create())
- [x] Optional arguments (FileService, SerliazeJson())
- [ ] Extension method (siūlau šito nedaryt)
- [x] Widening type casts (OffersController, Create())
- [ ] Narrowing type casts (nesugalvoju kur šitą panaudot, nes mes neturim normalių base klasių...)
- [x] Standard interfaces (IEquatable already implemented, IComparable for Offer)
