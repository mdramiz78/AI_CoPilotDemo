# ramiz tedst ########

### TC-001: View bookings list with existing bookings
**Category**: Happy Path
**Priority**: P0
**Preconditions**: User is logged in; user has at least one confirmed booking
**Steps**:
1. Navigate to `/bookings`.
2. Observe the bookings list.
**Expected Results**: Booking cards appear with booking reference, event name, quantity, total price, status, and a "View Details" action.
**Business Rule**: Users should be able to see all of their own bookings.
**Suggested Layer**: E2E

### TC-002: View booking detail page shows all sections
**Category**: Happy Path
**Priority**: P0
**Preconditions**: User is logged in; user has a confirmed booking
**Steps**:
1. Navigate to `/bookings`.
2. Click "View Details" on an existing booking.
3. Verify the booking detail page loads.
**Expected Results**: The page displays the booking reference, status badge, event details, customer details, payment summary, refund eligibility control, and booking metadata.
**Business Rule**: Booking detail UI must surface the full booking record and refund eligibility action.
**Suggested Layer**: E2E

### TC-003: Cancel a booking from the detail page
**Category**: Happy Path
**Priority**: P0
**Preconditions**: User is logged in; user has a confirmed booking
**Steps**:
1. Navigate to the booking detail page for the booking.
2. Click "Cancel Booking".
3. Confirm cancellation in the dialog.
**Expected Results**: The booking is cancelled, a success toast appears, the user is redirected to `/bookings`, and the cancelled booking no longer appears in the list.
**Business Rule**: Cancelling a booking removes it from the user’s bookings and updates available seats appropriately.
**Suggested Layer**: E2E

### TC-004: Clear all bookings and show empty state
**Category**: Happy Path
**Priority**: P0
**Preconditions**: User is logged in; user has at least one booking
**Steps**:
1. Navigate to `/bookings`.
2. Click "Clear all bookings" and accept the confirmation.
**Expected Results**: All bookings are removed, the page displays an empty state with "No bookings yet", and a "Browse Events" action is visible.
**Business Rule**: Clearing bookings removes all of the current user's bookings.
**Suggested Layer**: E2E

### TC-100: Booking reference starts with event title first letter
**Category**: Business Rule
**Priority**: P0
**Preconditions**: User is logged in; an event is available for booking
**Steps**:
1. Book an event.
2. Read the booking reference on the confirmation page.
**Expected Results**: The booking reference begins with the uppercase first character of the booked event title, followed by a dash and a 6-character code.
**Business Rule**: Booking reference prefix must match the event title first character.
**Suggested Layer**: E2E

### TC-200: Cross-user booking access returns Access Denied
**Category**: Security
**Priority**: P0
**Preconditions**: Two valid user accounts exist; User A has at least one booking
**Steps**:
1. Log in as User A and note a booking ID or reference.
2. Log out and log in as User B.
3. Attempt to navigate to User A’s booking detail page.
**Expected Results**: The page shows "Access Denied" and the booking details are not exposed.
**Business Rule**: Users may only access their own bookings; cross-user booking access is forbidden.
**Suggested Layer**: E2E
