# Testing Ecosystem ✅

Planet Nine includes a sophisticated multi-phase testing system that validates the entire distributed infrastructure across all components.

## Overview

**Location**: `/allyabase/deployment/docker/`

The testing system provides end-to-end validation through 6 comprehensive phases, ensuring that all components of the Planet Nine ecosystem work together seamlessly in production environments.

## Complete Ecosystem Testing ✅

### Testing Architecture

#### 6-Phase Validation System
1. **Infrastructure Setup** - Start 3 allyabase instances with different port configurations
2. **Service Validation** - Test all 12+ microservices across all bases
3. **Application Testing** - Validate all Nullary applications on each base
4. **Cross-Base Interaction** - Test P2P connections and content aggregation across bases
5. **Nexus Portal Visual Demonstration** - Launch web-based ecosystem showcase with browser automation
6. **Integration Validation** - Generate comprehensive reports and validate ecosystem health

### Quick Start Testing

```bash
# Complete ecosystem validation
cd allyabase/deployment/docker
./test-complete-ecosystem.sh

# Test with debugging enabled
./test-complete-ecosystem.sh --continue-on-failure --apps=core

# Test individual components
./test-all-bases.sh --build                    # Infrastructure only
./test-all-services.sh 1000                    # Services on Base 1
cd nullary-tests && ./test-rhapsold.sh 1000    # Individual app testing
```

### Test Coverage

#### ✅ Multi-Base Infrastructure
- **3 Independent Bases**: Complete allyabase instances with port isolation
- **Container Networking**: Docker-based reproducible testing environment
- **Port Management**: Automatic port allocation and conflict resolution
- **Health Monitoring**: Continuous service health checks during testing

#### ✅ Service Integration Testing
- **All Microservices**: BDO, Sanora, Addie, Fount, Dolores, Covenant, and more
- **Cross-Service Communication**: API integration testing between services
- **Authentication Testing**: Sessionless protocol validation across all services
- **Data Persistence**: Storage and retrieval testing across service restarts

#### ✅ Application Validation
- **Complete Nullary Suite**: Rhapsold, StackChat, Lexary, Photary, Ninefy, MyBase
- **Real Service Integration**: No mock data - all apps tested against real services
- **Cross-Platform Testing**: Tauri applications across multiple environments
- **UI/UX Validation**: SVG component system and user interaction testing

#### ✅ Cross-Base P2P Testing
- **StackChat Messaging**: P2P communication across different bases
- **Cryptographic Handshakes**: End-to-end encryption validation
- **Message Routing**: Cross-base message delivery and receipt confirmation
- **Identity Verification**: Sessionless authentication across base boundaries

#### ✅ Content Aggregation Testing
- **MyBase Integration**: Content pulling from multiple independent bases
- **Teleportation Protocol**: Cross-base content discovery and verification
- **Feed Aggregation**: Real-time content streaming from multiple sources
- **Data Synchronization**: Consistency validation across distributed data

#### ✅ CI/CD Ready Infrastructure
- **Docker-Based**: Completely containerized testing environment
- **Reproducible Results**: Consistent testing across different environments
- **Comprehensive Reporting**: Detailed logs and validation reports
- **Automated Cleanup**: Complete environment teardown after testing

## Testing Infrastructure

### Docker Container Architecture

#### Base Configuration
```yaml
# 3-Base Docker Setup
Base 1: Ports 5114-5118
  - BDO: 5117
  - Sanora: 5118
  - Addie: 5116
  - Fount: 5116

Base 2: Ports 5119-5123
  - BDO: 5122
  - Sanora: 5123
  - Addie: 5121
  - Fount: 5121

Base 3: Ports 5124-5128
  - BDO: 5127
  - Sanora: 5128
  - Addie: 5126
  - Fount: 5126
```

#### Container Networking
```bash
# Docker network creation
docker network create planet-nine-test

# Container startup with networking
docker run --name base1-bdo --network planet-nine-test -p 5117:3003 planet-nine/bdo
docker run --name base1-sanora --network planet-nine-test -p 5118:7243 planet-nine/sanora
```

### Test Orchestration Scripts

#### Master Test Script
**File**: `test-complete-ecosystem.sh`

```bash
#!/bin/bash
# Complete ecosystem testing orchestration

# Phase 1: Infrastructure
echo "🏗️ Phase 1: Infrastructure Setup"
./test-all-bases.sh --build

# Phase 2: Services
echo "🔧 Phase 2: Service Validation"
for base in 1000 2000 3000; do
    ./test-all-services.sh $base
done

# Phase 3: Applications
echo "📱 Phase 3: Application Testing"
cd nullary-tests
./test-all-apps.sh

# Phase 4: Cross-Base
echo "🌐 Phase 4: Cross-Base Interaction"
./test-cross-base.sh

# Phase 5: Nexus Portal
echo "🎭 Phase 5: Nexus Portal Demonstration"
./test-nexus-portal.sh

# Phase 6: Integration
echo "✅ Phase 6: Integration Validation"
./validate-ecosystem.sh
```

#### Service Testing Scripts
**Location**: `nullary-tests/`

```bash
# Individual application testing
./test-rhapsold.sh 1000      # Test Rhapsold on Base 1
./test-stackchat.sh 1000     # Test StackChat on Base 1
./test-ninefy.sh 1000        # Test Ninefy on Base 1
./test-mybase.sh 1000        # Test MyBase aggregation

# Cross-base testing
./test-stackchat-p2p.sh      # P2P messaging across bases
./test-mybase-aggregation.sh # Content aggregation testing
./test-teleportation.sh      # Cross-base content discovery
```

## Test Scenarios

### Service-Level Testing

#### BDO (Big Dumb Object) Testing
```bash
# Test object storage across all bases
test_bdo_storage() {
    for base_port in 5117 5122 5127; do
        # Store object
        response=$(curl -X PUT "http://127.0.0.1:$base_port/bdo" \
            -H "Content-Type: application/json" \
            -d '{"test": "data"}')

        # Verify storage
        uuid=$(echo $response | jq -r '.uuid')
        stored=$(curl "http://127.0.0.1:$base_port/bdo/$uuid")

        # Validate data integrity
        assert_equals "$(echo $stored | jq -r '.test')" "data"
    done
}
```

#### Sanora (Product Hosting) Testing
```bash
# Test product management across bases
test_sanora_products() {
    for base_port in 5118 5123 5128; do
        # Create product
        product=$(curl -X POST "http://127.0.0.1:$base_port/product" \
            -H "Content-Type: application/json" \
            -d '{"title": "Test Product", "price": 1999}')

        # Verify product listing
        products=$(curl "http://127.0.0.1:$base_port/products/base")
        assert_contains "$products" "Test Product"

        # Test teleportable feed
        feed=$(curl "http://127.0.0.1:$base_port/teleportable-products")
        assert_valid_html "$feed"
    done
}
```

### Application-Level Testing

#### Rhapsold (Blogging) Testing
```javascript
// Test blog creation and management
async function testRhapsoldBlogging(basePort) {
    // Test blog post creation
    const createResponse = await fetch(`http://127.0.0.1:${basePort}/blog`, {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({
            title: 'Test Blog Post',
            content: 'This is a test blog post content.',
            author: 'Test Author'
        })
    });

    assert(createResponse.ok, 'Blog post creation failed');

    // Test blog post retrieval
    const blogId = (await createResponse.json()).id;
    const getResponse = await fetch(`http://127.0.0.1:${basePort}/blog/${blogId}`);
    const blog = await getResponse.json();

    assert(blog.title === 'Test Blog Post', 'Blog title mismatch');
    assert(blog.content.includes('test blog post'), 'Blog content mismatch');
}
```

#### StackChat P2P Testing
```javascript
// Test cross-base messaging
async function testStackChatP2P() {
    // Create users on different bases
    const user1 = await createUser('http://127.0.0.1:5116'); // Base 1
    const user2 = await createUser('http://127.0.0.1:5121'); // Base 2

    // Send message from Base 1 to Base 2
    const message = {
        to: user2.pubKey,
        content: 'Cross-base test message',
        timestamp: Date.now()
    };

    const sendResponse = await sendMessage(user1, message, 'http://127.0.0.1:5116');
    assert(sendResponse.success, 'Message sending failed');

    // Verify message receipt on Base 2
    const messages = await getMessages(user2, 'http://127.0.0.1:5121');
    assert(messages.some(m => m.content === 'Cross-base test message'), 'Message not received');
}
```

### Cross-Base Integration Testing

#### MyBase Content Aggregation
```javascript
// Test content aggregation from multiple bases
async function testMyBaseAggregation() {
    const bases = [
        'http://127.0.0.1:5116',
        'http://127.0.0.1:5121',
        'http://127.0.0.1:5126'
    ];

    // Create content on each base
    for (const base of bases) {
        await createTestContent(base);
    }

    // Test aggregation
    const aggregatedContent = await aggregateContent(bases);

    assert(aggregatedContent.length >= 3, 'Insufficient aggregated content');
    assert(aggregatedContent.every(c => c.verified), 'Unverified content in aggregation');
}
```

#### Teleportation Protocol Testing
```javascript
// Test cross-base content discovery
async function testTeleportation() {
    // Create teleportable content on Base 1
    const content = await createTeleportableContent('http://127.0.0.1:5118');

    // Request teleportation from Base 2
    const teleportResponse = await requestTeleportation(
        'http://127.0.0.1:5122',
        content.url,
        content.pubKey
    );

    assert(teleportResponse.valid, 'Teleportation signature validation failed');
    assert(teleportResponse.content.includes('<teleportal'), 'Invalid teleported content');
}
```

## Performance Testing

### Load Testing Scripts

#### Service Load Testing
```bash
# Test service performance under load
test_service_load() {
    local service_url=$1
    local concurrent_users=10
    local requests_per_user=100

    # Use artillery for load testing
    artillery quick \
        --count $concurrent_users \
        --num $requests_per_user \
        $service_url
}
```

#### Database Performance Testing
```bash
# Test BDO storage performance
test_bdo_performance() {
    local base_port=$1
    local num_objects=1000

    start_time=$(date +%s)

    for i in $(seq 1 $num_objects); do
        curl -X PUT "http://127.0.0.1:$base_port/bdo" \
            -H "Content-Type: application/json" \
            -d "{\"test_object\": $i}" > /dev/null 2>&1
    done

    end_time=$(date +%s)
    duration=$((end_time - start_time))

    echo "Stored $num_objects objects in $duration seconds"
    echo "Rate: $((num_objects / duration)) objects/second"
}
```

### Memory and Resource Testing

#### Memory Leak Detection
```javascript
// Monitor memory usage during testing
class MemoryMonitor {
    constructor() {
        this.initialMemory = process.memoryUsage();
        this.samples = [];
    }

    sample() {
        const current = process.memoryUsage();
        const growth = {
            rss: current.rss - this.initialMemory.rss,
            heapUsed: current.heapUsed - this.initialMemory.heapUsed,
            timestamp: Date.now()
        };
        this.samples.push(growth);
    }

    checkForLeaks() {
        const recentSamples = this.samples.slice(-10);
        const avgGrowth = recentSamples.reduce((sum, s) => sum + s.heapUsed, 0) / recentSamples.length;

        if (avgGrowth > 50 * 1024 * 1024) { // 50MB growth
            throw new Error(`Potential memory leak detected: ${avgGrowth} bytes average growth`);
        }
    }
}
```

## Test Reporting

### Comprehensive Test Reports

#### Test Results Format
```json
{
    "testRun": {
        "timestamp": "2025-01-21T10:30:00Z",
        "duration": "24.5 minutes",
        "phases": {
            "infrastructure": {
                "status": "PASSED",
                "duration": "3.2 minutes",
                "details": "3 bases started successfully"
            },
            "services": {
                "status": "PASSED",
                "duration": "8.7 minutes",
                "tested": 12,
                "passed": 12,
                "failed": 0
            },
            "applications": {
                "status": "PASSED",
                "duration": "6.1 minutes",
                "tested": 8,
                "passed": 8,
                "failed": 0
            },
            "crossBase": {
                "status": "PASSED",
                "duration": "4.3 minutes",
                "p2pMessages": 150,
                "aggregatedContent": 45
            },
            "nexusPortal": {
                "status": "PASSED",
                "duration": "1.8 minutes",
                "browsersLaunched": 1,
                "demonstrationsCompleted": 4
            },
            "integration": {
                "status": "PASSED",
                "duration": "0.4 minutes",
                "validationsCompleted": 25
            }
        }
    }
}
```

#### Automated Report Generation
```bash
# Generate comprehensive test report
generate_test_report() {
    cat > test-report.md << EOF
# Planet Nine Ecosystem Test Report

**Test Run**: $(date)
**Duration**: $TEST_DURATION
**Overall Status**: $OVERALL_STATUS

## Phase Results

### 🏗️ Infrastructure Setup
- **Status**: $INFRASTRUCTURE_STATUS
- **Bases Started**: $BASES_STARTED
- **Port Conflicts**: $PORT_CONFLICTS

### 🔧 Service Validation
- **Services Tested**: $SERVICES_TESTED
- **Services Passed**: $SERVICES_PASSED
- **Service Failures**: $SERVICE_FAILURES

### 📱 Application Testing
- **Apps Tested**: $APPS_TESTED
- **Apps Passed**: $APPS_PASSED
- **App Failures**: $APP_FAILURES

### 🌐 Cross-Base Interaction
- **P2P Messages**: $P2P_MESSAGES
- **Content Aggregation**: $CONTENT_AGGREGATED
- **Teleportation Tests**: $TELEPORTATION_TESTS

EOF
}
```

## Key Testing Documentation

### Master Documentation Files
- **[README-COMPLETE-TESTING.md](/allyabase/deployment/docker/README-COMPLETE-TESTING.md)** - Master testing guide
- **[README-INTEGRATED-TESTING.md](/allyabase/deployment/docker/README-INTEGRATED-TESTING.md)** - Docker service testing
- **[nullary-tests/README.md](/allyabase/deployment/docker/nullary-tests/README.md)** - Application testing framework
- **[TEST_THOUGHTS.md](/TEST_THOUGHTS.md)** - Original testing strategy documentation

### Test Configuration Files
```
deployment/docker/
├── test-complete-ecosystem.sh    # Master test orchestration
├── test-all-bases.sh            # Infrastructure testing
├── test-all-services.sh         # Service validation
├── validate-ecosystem.sh        # Integration validation
├── nullary-tests/
│   ├── test-all-apps.sh         # Application testing
│   ├── test-rhapsold.sh         # Individual app tests
│   ├── test-stackchat.sh        # P2P testing
│   ├── test-cross-base.sh       # Cross-base validation
│   └── test-nexus-portal.sh     # Web portal testing
└── reports/
    ├── test-results.json        # Structured results
    ├── performance-metrics.json # Performance data
    └── coverage-report.html     # Test coverage
```

## Continuous Integration

### CI/CD Integration
```yaml
# GitHub Actions workflow
name: Planet Nine Ecosystem Tests
on: [push, pull_request]

jobs:
  ecosystem-test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2

      - name: Setup Docker
        uses: docker/setup-buildx-action@v1

      - name: Run Complete Ecosystem Tests
        run: |
          cd allyabase/deployment/docker
          ./test-complete-ecosystem.sh

      - name: Upload Test Reports
        uses: actions/upload-artifact@v2
        with:
          name: test-reports
          path: reports/
```

### Automated Quality Gates
```bash
# Quality gate validation
validate_quality_gates() {
    local test_results=$1

    # Check test pass rate
    local pass_rate=$(jq '.passRate' $test_results)
    if (( $(echo "$pass_rate < 0.95" | bc -l) )); then
        echo "❌ Test pass rate below 95%: $pass_rate"
        exit 1
    fi

    # Check performance benchmarks
    local avg_response_time=$(jq '.avgResponseTime' $test_results)
    if (( $(echo "$avg_response_time > 1000" | bc -l) )); then
        echo "❌ Average response time above 1000ms: $avg_response_time"
        exit 1
    fi

    echo "✅ All quality gates passed"
}
```

The Planet Nine testing ecosystem ensures that all components work together seamlessly, providing confidence for production deployments and enabling rapid development while maintaining system reliability and performance.