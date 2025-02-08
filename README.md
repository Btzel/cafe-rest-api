# Cafe REST API
A RESTful API built with Flask and SQLAlchemy that manages cafe data, including locations, amenities, and prices.

![Python](https://img.shields.io/badge/Python-3.8+-blue)
![Flask](https://img.shields.io/badge/Flask-Backend-red)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-Database-green)
![REST](https://img.shields.io/badge/REST-API-orange)

## 🎯 Overview
This educational project implements a RESTful API that demonstrates:
1. Basic CRUD operations
2. Database management with SQLAlchemy
3. API endpoint creation and handling
4. HTTP methods implementation
5. Response formatting and status codes

📚 **Educational Purpose**: This project was created to understand RESTful API concepts and implementation. It serves as a learning tool for understanding API development with Flask.

🔗 **API Documentation**: [View the complete Postman documentation](https://documenter.getpostman.com/view/41956845/2sAYX9kepf#ed83bc35-2f83-43de-9b5c-22dd0133d4a9)

## 🌐 API Endpoints
### GET Endpoints
- `/random`: Get a random cafe
- `/all`: Get all cafes
- `/search?loc=<location>`: Search cafes by location

### POST Endpoints
- `/add`: Add a new cafe
  ```json
  {
    "name": "Cafe Name",
    "map_url": "URL",
    "img_url": "URL",
    "loc": "Location",
    "sockets": true,
    "toilet": true,
    "wifi": true,
    "calls": true,
    "seats": "0-10",
    "coffee_price": "£2.50"
  }
  ```

### PATCH Endpoints
- `/update-price/<cafe_id>?new_price=<price>`: Update cafe price

### DELETE Endpoints
- `/report-closed/<cafe_id>?api-key=<key>`: Delete a cafe

## 🔧 Technical Components
### Database Model
```python
class Cafe(db.Model):
    id: Mapped[int] = mapped_column(Integer, primary_key=True)
    name: Mapped[str] = mapped_column(String(250), unique=True, nullable=False)
    map_url: Mapped[str] = mapped_column(String(500), nullable=False)
    img_url: Mapped[str] = mapped_column(String(500), nullable=False)
    location: Mapped[str] = mapped_column(String(250), nullable=False)
    seats: Mapped[str] = mapped_column(String(250), nullable=False)
    has_toilet: Mapped[bool] = mapped_column(Boolean, nullable=False)
    has_wifi: Mapped[bool] = mapped_column(Boolean, nullable=False)
    has_sockets: Mapped[bool] = mapped_column(Boolean, nullable=False)
    can_take_calls: Mapped[bool] = mapped_column(Boolean, nullable=False)
    coffee_price: Mapped[str] = mapped_column(String(250), nullable=True)
```

### Key Features
1. **Database Operations**
   - CRUD functionality
   - SQLAlchemy integration
   - Data validation
   - Error handling

2. **API Security**
   - API key authentication
   - Error responses
   - Status codes
   - Input validation

3. **Search Functionality**
   - Location-based search
   - Random cafe selection
   - Full cafe listing
   - Price updates

## 💻 Implementation Details
### Technologies Used
- Flask for API framework
- SQLAlchemy ORM
- SQLite database
- RESTful architecture

### Response Format
All responses are in JSON format:
```json
{
    "cafe": {
        "id": 1,
        "name": "Cafe Name",
        "location": "Location",
        "amenities": {
            "wifi": true,
            "toilet": true
        }
    }
}
```

## 🚀 Usage
1. Install required packages:
```bash
pip install flask flask-sqlalchemy
```

2. Initialize database:
```python
python main.py
```

3. Test API endpoints:
- Using Postman: Import the [collection](https://documenter.getpostman.com/view/41956845/2sAYX9kepf#ed83bc35-2f83-43de-9b5c-22dd0133d4a9)
- Using curl:
```bash
# Get all cafes
curl http://localhost:5000/all

# Search cafe by location
curl http://localhost:5000/search?loc=London

# Add new cafe
curl -X POST -F "name=New Cafe" -F "map_url=http://example.com" [...] http://localhost:5000/add

# Update price
curl -X PATCH http://localhost:5000/update-price/1?new_price=£2.50

# Delete cafe (requires API key)
curl -X DELETE http://localhost:5000/report-closed/1?api-key=my37spper*api*key''34
```

## 🎯 API Rules
1. Use valid API key for deletions
2. Provide all required fields for POST
3. Use proper HTTP methods
4. Handle error responses
5. Validate input data

## 🛠️ Project Structure
```
cafe-api/
├── main.py           # API implementation
├── instance/         # SQLite database
│   └── cafes.db     
└── templates/        # HTML templates
```

## 📊 Features
### Input Handling
- Form data processing
- Query parameter parsing
- API key validation
- Data type conversion

### Output Management
- JSON responses
- Error messages
- Status codes
- Success feedback

## 📝 License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👥 Author
Burak TÜZEL