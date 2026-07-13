# TrackPlay Integrations Documentation

This directory contains comprehensive user documentation for TrackPlay's integration and conversion tracking system.

## Documentation Structure

### Core Integration Guides
- **[Overview](./overview.mdx)** - Introduction to TrackPlay integrations and how they work
- **[Configuration](./configuration.mdx)** - Comprehensive setup and configuration guide
- **[Conversion Tracking](./conversion-tracking.mdx)** - Deep dive into how conversion tracking works

### Platform-Specific Guides
- **[Buygoods Integration](./buygoods.mdx)** - Complete setup guide for Buygoods
- **[Clickbank Integration](./clickbank.mdx)** - Complete setup guide for Clickbank
- **[ElasticFunnels Integration](./elasticfunnels.mdx)** - Guide for ElasticFunnels enhancement

### Analytics and Reporting
- **[Analytics Guide](./analytics.mdx)** - Understanding and using conversion analytics
- **[Quick Start](./quick-start.mdx)** - Basic integration setup for new users

## Supported Integrations

### Payment Processors
1. **Buygoods** - E-commerce platform for digital products
2. **Clickbank** - Digital marketplace and affiliate network
3. **Digistore24** - Digital product marketplace (referenced but not fully implemented)

### Enhancement Platforms
1. **ElasticFunnels.io** - Funnel optimization that enhances other integrations

### AI & Media
1. **[ElevenLabs & AI Segments](./elevenlabs-ai-segments.mdx)** - ElevenLabs API key and time-based personalized TTS in the player

## Key Features Documented

### Automatic Tracking
- Session ID generation for each video viewer
- Automatic modification of purchase links and forms
- Real-time parameter injection with tracking data

### Conversion Capture
- Comprehensive conversion data collection
- Support for sales, refunds, and chargebacks
- Customer and product information tracking
- Geographic and device analytics

### Security & Privacy
- Encrypted data transmission (Clickbank)
- Unique postback URLs for secure communication

### Analytics & Reporting
- Video-level and workspace-level analytics
- Revenue metrics and conversion rates
- Geographic and demographic insights
- Cross-platform attribution

## Integration Workflow

1. **Activation** - Activate desired integrations in TrackPlay dashboard
2. **Configuration** - Set tracking parameters and encryption keys
3. **Postback Setup** - Configure payment processor postback URLs
4. **Testing** - Verify tracking with test transactions
5. **Monitoring** - Track performance through TrackPlay analytics

## User Experience Focus

This documentation is written for end users and focuses on:
- Step-by-step setup instructions
- User interface guidance
- Troubleshooting common issues
- Best practices for optimization
- Security and privacy considerations

## Technical Implementation Notes

The underlying system includes:
- JavaScript-based link modification (`ConversionTracking.js`)
- Frontend Vue.js components for configuration
- Real-time status monitoring
- Comprehensive analytics system
- Secure data handling and transmission

## Support Resources

- Email support: support@trackplay.io
- Integration-specific troubleshooting guides
- Status monitoring and health checks
- Test transaction capabilities