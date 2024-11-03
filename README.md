# YouTube Analytics Backend

A serverless backend implementation for YTAnalytics.com, processing and analyzing YouTube video metrics using AWS Lambda and DynamoDB.


## 🎥 Demo 
[![Demo Video](https://img.shields.io/badge/Watch%20Demo-red?style=for-the-badge&logo=youtube)](https://www.youtube.com/watch?v=hoaRQoU7iuE)
The [demo video](https://www.youtube.com/watch?v=hoaRQoU7iuE) provides a comprehensive walkthrough of YTAnalytics in action, featuring:
- Live analysis of a trending YouTube video
- Real-time metric extraction and processing
- Demonstration of key features:
  - Instant video statistics analysis
  - Channel performance metrics
  - Engagement rate calculations
  - Geographic viewer distribution


## 🏗️ Architecture Evolution

### Current Architecture (Serverless Microservices)
- **AWS Lambda Functions** for serverless compute
- **Amazon DynamoDB** for serverless NoSQL database
- **API Gateway** for REST API endpoints
- **YouTube Data API** integration
- Complete serverless architecture for maximum cost optimization

### Previous Architecture (Monolithic)
- Flask server on EC2 instance
- SQLite database
- Single instance deployment
- Fixed cost model regardless of usage

## 🚀 Features

### API Endpoints

#### 1. `/getPerson` (GET)
- Processes new YouTube video URLs
- Extracts video and channel statistics
- Stores data in DynamoDB
- Returns comprehensive analytics

#### 2. `/getPrevData` (GET)
- Retrieves random historical analysis
- Implements data cycling mechanism
- Maintains data freshness

#### 3. `/getLaunch` (GET)
- Retrieves most recent analysis
- Used for initial application load

### Data Processing
- Video statistics extraction
- Channel metrics analysis
- Engagement metrics calculation
- Geographic distribution tracking

## 🛠️ Technical Stack

### Core Technologies
- Python 3.8+
- AWS Lambda
- Amazon DynamoDB
- YouTube Data API v3
- AWS API Gateway

### Key Dependencies
- `boto3`: AWS SDK for DynamoDB operations
- `googleapiclient`: YouTube API integration
- `json`: Data serialization
- `re`: URL parsing

## 📦 Project Structure

```
YtAnalytics.com_Backend/
├── lambda_function.py      # Main Lambda handler
├── requirements.txt        # Python dependencies
└── dynamodb/
    └── schema.json        # DynamoDB table definitions
```

## 🔧 DynamoDB Schema

```json
{
    "TableName": "YTAnalytics",
    "KeySchema": [
        {
            "AttributeName": "id",
            "KeyType": "HASH"
        },
        {
            "AttributeName": "timestamp",
            "KeyType": "RANGE"
        }
    ],
    "AttributeDefinitions": [
        {
            "AttributeName": "id",
            "AttributeType": "S"
        },
        {
            "AttributeName": "timestamp",
            "AttributeType": "N"
        }
    ],
    "ProvisionedThroughput": {
        "ReadCapacityUnits": "1",
        "WriteCapacityUnits": "1"
    }
}
```

## 🚀 Deployment

### Prerequisites
1. AWS Account with appropriate permissions
2. YouTube Data API credentials
3. Python 3.8+ environment

### AWS Lambda Setup
1. Create new Lambda function
2. Set Python 3.8+ runtime
3. Configure environment variables:
   - `DYNAMODB_TABLE`
   - `YOUTUBE_API_KEY`
4. Set appropriate memory and timeout settings
5. Configure API Gateway trigger

### DynamoDB Setup
1. Create table with schema
2. Configure auto-scaling
3. Set up on-demand capacity mode
4. Enable point-in-time recovery (optional)

## 📊 Performance Metrics

- Average response time: < 2 seconds
- Concurrent request handling: Auto-scaling
- Database operations: Single-digit millisecond performance
- Cost optimization: True pay-per-use model

## 🔒 Security

- API Key authentication
- DynamoDB encryption at rest
- IAM role-based access
- Environment variable encryption
- AWS WAF integration (optional)

## 💰 Cost Optimization

### AWS Lambda
- Automatic scaling
- Pay-per-execution model
- Optimized memory allocation

### Amazon DynamoDB
- On-demand capacity mode
- Auto-scaling capabilities
- No minimum fee
- Pay only for actual usage
- Significant cost savings compared to traditional databases

### Migration Benefits
- Eliminated fixed EC2 costs
- Removed database maintenance overhead
- Automatic scaling handles traffic spikes
- Pay only for actual usage
- Zero upfront infrastructure costs


## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 📧 Contact

Project Link: [https://github.com/saadzaki7/YtAnalytics.com_Backend](https://github.com/saadzaki7/YtAnalytics.com_Backend)
