# Scam Check Document Upload Service

A production-grade Spring Boot microservice for handling document uploads in the scam check system. This service provides secure, scalable, and efficient document processing capabilities with comprehensive validation, NSFW content checking, and Google Cloud Storage integration.

## Features

- **High Performance**: Optimized for 100+ TPS with asynchronous processing
- **Secure Upload**: Comprehensive file validation and security checks
- **NSFW Detection**: Integrated content moderation (placeholder implementation)
- **Cloud Storage**: Google Cloud Storage integration with organized folder structure
- **Monitoring**: Comprehensive metrics, health checks, and observability
- **Documentation**: Complete OpenAPI/Swagger documentation
- **Testing**: Comprehensive unit and integration tests

## Architecture

### Technology Stack
- **Java 17**: Latest LTS version for optimal performance
- **Spring Boot 3.2.0**: Modern framework with native compilation support
- **Google Cloud Storage**: Scalable cloud storage solution
- **MapStruct**: Type-safe mapping between DTOs
- **Micrometer**: Metrics and observability
- **JUnit 5**: Modern testing framework

### Design Principles
- **SOLID Principles**: Clean, maintainable, and extensible code
- **12-Factor App**: Cloud-native application design
- **Domain-Driven Design**: Clear separation of concerns
- **Defensive Programming**: Comprehensive validation and error handling

## API Documentation

### POST /economic-crime-prevention/resolving-fraud/scamcheck/v1/documents

Uploads a ZIP file containing images for scam check analysis.

#### Headers
- `x-org-id` (required): Organization or bank identifier
- `scam-check-session-id` (required): UUID for unique scam check session
- `x-abc-brand` (optional): Brand identifier for ABC bank
- `x-abc-channel` (optional): Channel identifier (Web/Mobile)

#### Request Body
- Multipart file upload with ZIP file (max 30MB)
- ZIP must contain 1-4 image files (JPEG, PNG, GIF, BMP)

#### Response

{
"success": true,
"scamCheckSessionId": "550e8400-e29b-41d4-a716-446655440000",
"storagePath": "gs://clean-image-gcs-bucket/550e8400.../document.zip",
"imageCount": 4,
"fileSizeBytes": 25165824,
"nsfwDetected": false,
"processedAt": "2025-07-29T12:30:45",
"processingTimeMs": 1250,
"message": "Document uploaded successfully"
}


## Configuration

### Environment Variables
GCS_PROJECT_ID=your-gcs-project
GCS_BUCKET_NAME=clean-image-gcs-bucket
GOOGLE_APPLICATION_CREDENTIALS=/path/to/credentials.json

### Application Properties
See `application.yml` for complete configuration options.

## Running the Application

### Prerequisites
- Java 17+
- Maven 3.8+
- Google Cloud Platform account with Storage API enabled

### Local Development

Clone the repository
git clone <repository-url>

Navigate to project directory
cd scam-check-document-service

Run tests
mvn test

Run the application
mvn spring-boot:run

### Docker
Build image
docker build -t scam-check-document-service .

Run container
docker run -p 8080:8080 scam-check-document-service


## Testing

### Test Coverage
- Unit tests for all service layers
- Integration tests for complete workflows
- Performance tests for TPS validation
- Security tests for validation logic

### Running Tests
Run all tests
mvn test

Run with coverage
mvn test jacoco:report


## Monitoring & Observability

### Health Checks
- Application health: `/actuator/health`
- Custom health indicators for GCS connectivity

### Metrics
- Prometheus metrics: `/actuator/prometheus`
- Custom business metrics for upload success/failure rates
- Performance metrics for processing times

### Logging
- Structured JSON logging
- Correlation IDs for request tracing
- Security audit logs

## Security Considerations

- Input validation and sanitization
- Path traversal attack prevention
- File type and size restrictions
- NSFW content detection
- Secure credential management

## Performance Optimization

- Asynchronous processing for NSFW checks
- Optimized thread pool configuration
- Memory-efficient file handling
- Connection pooling for GCS operations

## Troubleshooting

### Common Issues
1. **File size exceeded**: Check `spring.servlet.multipart.max-file-size`
2. **GCS authentication**: Verify `GOOGLE_APPLICATION_CREDENTIALS`
3. **High memory usage**: Review thread pool and file handling

### Logs
Check application logs for detailed error information and processing traces.

## Contributing

1. Follow existing code style and patterns
2. Add comprehensive tests for new features
3. Update documentation for API changes
4. Ensure all security validations are maintained

## License

Proprietary - Internal use only