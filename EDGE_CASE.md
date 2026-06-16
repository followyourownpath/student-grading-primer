# Document your edge case here
- To get marks for this section you will need to explain to your tutor:
1) The edge case you identified:
   **Calculating stats on an empty database (or when no students have marks)**
   If there are no students in the database, attempting to calculate the `average` will result in a Division by Zero error. Furthermore, functions like `min()` and `max()` will throw a `ValueError` if passed an empty sequence. This would result in a 500 Internal Server Error when calling `GET /stats`.

2) How you have accounted for this in your implementation:
   In the `GET /stats` route in `backend/app.py`, I added a check to verify if the list of students (or the list of their marks) is empty. If it is empty, the route safely bypasses the calculation and returns a default JSON object: `{ "count": 0, "average": 0, "min": 0, "max": 0 }`. This ensures the endpoint always returns a valid and expected JSON structure without crashing the server.