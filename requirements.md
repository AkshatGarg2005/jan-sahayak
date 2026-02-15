# Requirements Document: Jan-Sahayak (Voice-First Civil Caseworker)

 

## Introduction

 

Jan-Sahayak is a voice-first, vernacular AI agent designed to bridge the welfare scheme utilization gap across India. The system enables citizens to discover their eligibility for government welfare schemes across multiple sectors—including agriculture, disability support, women empowerment, health, and education scholarships—and generate filled application forms through natural voice conversations in local dialects, accessible via WhatsApp or toll-free numbers.

 

The core innovation is eliminating middlemen by automatically generating completed PDF application forms based on voice interactions, making welfare schemes accessible to citizens with literacy, language, and accessibility barriers across diverse socio-economic backgrounds.

 

## Glossary

 

- **Jan_Sahayak**: The voice-first AI system that assists citizens with welfare scheme discovery and application

- **Voice_Input_Module**: Component that captures and processes audio input from users

- **Speech_Recognition_Engine**: Component that converts vernacular speech to text

- **Intent_Classifier**: Component that maps user queries to relevant welfare schemes

- **Eligibility_Engine**: Component that evaluates user eligibility against scheme rules

- **Scheme_Database**: Repository containing welfare scheme information, rules, and requirements

- **Conversation_Manager**: Component that orchestrates multi-turn dialogues with users

- **Form_Generator**: Component that creates filled PDF application forms

- **Text_to_Speech_Engine**: Component that converts responses to vernacular speech

- **WhatsApp_Interface**: Integration layer for WhatsApp-based interactions

- **Toll_Free_Interface**: Integration layer for phone-based interactions

- **User_Profile**: Stored information about a citizen including demographics and documents

- **Scheme**: A government welfare program with eligibility criteria and application requirements

- **Application_Form**: A completed PDF document ready for submission

- **Vernacular_Language**: Local Indian languages and dialects (Bhojpuri, Maithili, Warli, Hindi, etc.)

- **Session**: A single conversation instance between user and Jan_Sahayak

- **Document_Requirement**: Specific documents needed to apply for a scheme

 

## Requirements

 

### Requirement 1: Voice Input Processing

 

**User Story:** As a rural citizen, I want to speak in my local dialect, so that I can communicate naturally without language barriers.

 

#### Acceptance Criteria

 

1. WHEN a user sends a voice message via WhatsApp, THE Voice_Input_Module SHALL accept audio files in common formats (MP3, OGG, AAC, WAV)

2. WHEN a user calls the toll-free number, THE Toll_Free_Interface SHALL capture voice input in real-time

3. WHEN audio quality is poor, THE Voice_Input_Module SHALL request the user to repeat their message

4. WHEN audio duration exceeds 2 minutes, THE Voice_Input_Module SHALL process it in segments

5. THE Voice_Input_Module SHALL support audio input in at least 10 vernacular languages including Hindi, Bhojpuri, Maithili, Marathi, Bengali, Tamil, Telugu, Gujarati, Punjabi, and Kannada

 

### Requirement 2: Speech Recognition and Transcription

 

**User Story:** As a rural citizen speaking in my dialect, I want the system to understand what I'm saying, so that I can get accurate responses.

 

#### Acceptance Criteria

 

1. WHEN audio input is received, THE Speech_Recognition_Engine SHALL transcribe it to text with minimum 85% accuracy for supported languages

2. WHEN dialect-specific vocabulary is detected, THE Speech_Recognition_Engine SHALL apply dialect-specific language models

3. WHEN transcription confidence is below 70%, THE Speech_Recognition_Engine SHALL flag the text for clarification

4. THE Speech_Recognition_Engine SHALL handle code-mixing between vernacular languages and Hindi/English

5. WHEN background noise is detected, THE Speech_Recognition_Engine SHALL apply noise reduction before transcription

 

### Requirement 3: Intent Recognition and Scheme Mapping

 

**User Story:** As a rural citizen describing my situation, I want the system to identify relevant welfare schemes, so that I don't miss benefits I'm eligible for.

 

#### Acceptance Criteria

 

1. WHEN a user describes their situation, THE Intent_Classifier SHALL identify at least one relevant welfare scheme category

2. WHEN multiple schemes are potentially relevant, THE Intent_Classifier SHALL rank them by relevance score

3. THE Intent_Classifier SHALL recognize common scenarios including agricultural distress, disability support needs, women-specific welfare, health needs, education scholarships, housing needs, employment needs, and pension eligibility

4. WHEN user intent is ambiguous, THE Conversation_Manager SHALL ask clarifying questions

5. THE Intent_Classifier SHALL map user queries to schemes across both central and state government programs

 

### Requirement 4: Eligibility Assessment

 

**User Story:** As a rural citizen, I want to know if I qualify for a scheme, so that I don't waste time on applications I'm not eligible for.

 

#### Acceptance Criteria

 

1. WHEN a scheme is identified, THE Eligibility_Engine SHALL evaluate user eligibility against all mandatory criteria

2. WHEN eligibility information is incomplete, THE Conversation_Manager SHALL ask for missing information through voice prompts

3. WHEN a user is eligible, THE Eligibility_Engine SHALL provide a confidence score (eligible/likely eligible/not eligible)

4. WHEN a user is not eligible, THE Eligibility_Engine SHALL explain which criteria are not met

5. THE Eligibility_Engine SHALL check eligibility for multiple schemes simultaneously when relevant

6. WHEN eligibility rules reference income thresholds, THE Eligibility_Engine SHALL use current year thresholds from the Scheme_Database

 

### Requirement 5: Conversational Dialogue Management

 

**User Story:** As a rural citizen, I want to have a natural conversation, so that I can provide information comfortably without filling complex forms.

 

#### Acceptance Criteria

 

1. WHEN a session starts, THE Conversation_Manager SHALL greet the user and ask how it can help

2. WHEN collecting information, THE Conversation_Manager SHALL ask one question at a time

3. WHEN a user provides an unclear answer, THE Conversation_Manager SHALL rephrase the question

4. THE Conversation_Manager SHALL maintain conversation context across multiple turns within a session

5. WHEN a user wants to go back, THE Conversation_Manager SHALL allow correction of previously provided information

6. WHEN a session is idle for more than 5 minutes, THE Conversation_Manager SHALL send a prompt asking if the user needs more help

7. THE Conversation_Manager SHALL support sessions lasting up to 30 minutes

 

### Requirement 6: Scheme Information Retrieval

 

**User Story:** As a rural citizen, I want to understand scheme benefits and requirements in simple language, so that I can make informed decisions.

 

#### Acceptance Criteria

 

1. WHEN a scheme is identified, THE Jan_Sahayak SHALL explain the scheme benefits in simple vernacular language

2. WHEN explaining requirements, THE Jan_Sahayak SHALL list all required documents clearly

3. THE Jan_Sahayak SHALL provide information about application deadlines when applicable

4. WHEN a user asks about scheme details, THE Jan_Sahayak SHALL retrieve information from the Scheme_Database

5. THE Scheme_Database SHALL contain information for at least 100 major central and state welfare schemes across agriculture, disability, women empowerment, health, and education sectors

 

### Requirement 7: Application Form Generation

 

**User Story:** As a rural citizen, I want a filled application form generated from my voice answers, so that I don't need to pay middlemen or struggle with paperwork.

 

#### Acceptance Criteria

 

1. WHEN all required information is collected, THE Form_Generator SHALL create a filled PDF application form

2. THE Form_Generator SHALL map voice-collected data to correct form fields

3. WHEN a form requires a signature, THE Form_Generator SHALL mark signature fields clearly

4. WHEN a form requires document attachments, THE Form_Generator SHALL list them on the form

5. THE Form_Generator SHALL generate forms that match official government templates

6. WHEN form generation is complete, THE Jan_Sahayak SHALL send the PDF via WhatsApp or provide download instructions

7. THE Form_Generator SHALL include a summary page listing all information filled and documents needed

 

### Requirement 8: Voice Response Generation

 

**User Story:** As a rural citizen, I want to hear responses in my own dialect, so that I can understand without reading text.

 

#### Acceptance Criteria

 

1. WHEN generating a response, THE Text_to_Speech_Engine SHALL convert text to speech in the user's selected language

2. THE Text_to_Speech_Engine SHALL use natural-sounding voices appropriate for the dialect

3. WHEN responding via WhatsApp, THE Jan_Sahayak SHALL send voice messages in addition to text

4. WHEN responding via toll-free number, THE Text_to_Speech_Engine SHALL stream audio in real-time

5. THE Text_to_Speech_Engine SHALL speak at a pace appropriate for rural users (slower than standard)

6. WHEN technical terms are unavoidable, THE Text_to_Speech_Engine SHALL pronounce them clearly

 

### Requirement 9: WhatsApp Integration

 

**User Story:** As a rural citizen with limited internet access, I want to use WhatsApp, so that I can access the service on my basic smartphone.

 

#### Acceptance Criteria

 

1. THE WhatsApp_Interface SHALL support interactions through WhatsApp Business API

2. WHEN a user sends a message, THE WhatsApp_Interface SHALL respond within 10 seconds

3. THE WhatsApp_Interface SHALL support both voice messages and text messages

4. WHEN sending PDFs, THE WhatsApp_Interface SHALL compress files to work on low bandwidth (under 2MB)

5. THE WhatsApp_Interface SHALL provide a menu of common queries for users who prefer structured navigation

6. WHEN a session is interrupted, THE WhatsApp_Interface SHALL allow users to resume within 24 hours

 

### Requirement 10: Toll-Free Number Integration

 

**User Story:** As a rural citizen without a smartphone, I want to call a toll-free number, so that I can access the service using any basic phone.

 

#### Acceptance Criteria

 

1. THE Toll_Free_Interface SHALL accept calls on a toll-free number accessible across India

2. WHEN a call is received, THE Toll_Free_Interface SHALL present an IVR menu for language selection

3. THE Toll_Free_Interface SHALL support voice conversations with real-time speech recognition and synthesis

4. WHEN call quality degrades, THE Toll_Free_Interface SHALL switch to DTMF input for critical information

5. WHEN a PDF is generated, THE Toll_Free_Interface SHALL send it via SMS link or offer to send via WhatsApp

6. THE Toll_Free_Interface SHALL handle at least 100 concurrent calls

 

### Requirement 11: User Profile Management

 

**User Story:** As a returning user, I want the system to remember my information, so that I don't have to repeat it for every scheme inquiry.

 

#### Acceptance Criteria

 

1. WHEN a user provides personal information, THE Jan_Sahayak SHALL ask permission to store it

2. WHEN permission is granted, THE Jan_Sahayak SHALL create a User_Profile linked to the phone number

3. WHEN a returning user starts a session, THE Jan_Sahayak SHALL retrieve their User_Profile

4. THE User_Profile SHALL store demographic information, document availability, and previous applications

5. WHEN a user requests, THE Jan_Sahayak SHALL delete their User_Profile completely

6. THE Jan_Sahayak SHALL encrypt all stored personal information

 

### Requirement 12: Scheme Database Management

 

**User Story:** As a system administrator, I want to update scheme information easily, so that users always get current and accurate information.

 

#### Acceptance Criteria

 

1. THE Scheme_Database SHALL store scheme information in a structured format including name, eligibility criteria, benefits, required documents, and application process

2. WHEN scheme rules change, THE Scheme_Database SHALL support versioning to track changes

3. THE Scheme_Database SHALL support adding new schemes without code changes

4. WHEN eligibility criteria are complex, THE Scheme_Database SHALL store them as evaluable rules

5. THE Scheme_Database SHALL include both central government and state-specific schemes

6. THE Scheme_Database SHALL tag schemes with relevant keywords for intent matching

 

### Requirement 13: Multi-Language Support

 

**User Story:** As a rural citizen, I want to switch languages during conversation, so that I can use the language I'm most comfortable with for different topics.

 

#### Acceptance Criteria

 

1. WHEN a session starts, THE Jan_Sahayak SHALL detect the user's language from their first message

2. WHEN language detection confidence is low, THE Jan_Sahayak SHALL ask the user to select their preferred language

3. WHEN a user switches languages mid-conversation, THE Jan_Sahayak SHALL adapt to the new language

4. THE Jan_Sahayak SHALL maintain consistent terminology across languages for scheme names

5. WHEN a scheme name has no vernacular translation, THE Jan_Sahayak SHALL use the official name with explanation

 

### Requirement 14: Error Handling and Fallback

 

**User Story:** As a rural citizen with limited technical knowledge, I want clear guidance when something goes wrong, so that I can still complete my task.

 

#### Acceptance Criteria

 

1. WHEN speech recognition fails, THE Jan_Sahayak SHALL ask the user to repeat or offer text input option

2. WHEN the system cannot identify user intent after 3 attempts, THE Jan_Sahayak SHALL offer to connect to a human operator

3. WHEN the Scheme_Database is unavailable, THE Jan_Sahayak SHALL inform the user and suggest trying later

4. WHEN form generation fails, THE Jan_Sahayak SHALL save the collected information and retry

5. WHEN network connectivity is lost during WhatsApp interaction, THE Jan_Sahayak SHALL resume from the last successful exchange

6. THE Jan_Sahayak SHALL log all errors for system improvement

 

### Requirement 15: Privacy and Data Security

 

**User Story:** As a rural citizen sharing personal information, I want my data to be secure, so that I can trust the system with sensitive details.

 

#### Acceptance Criteria

 

1. THE Jan_Sahayak SHALL encrypt all personal data in transit using TLS 1.3 or higher

2. THE Jan_Sahayak SHALL encrypt all personal data at rest using AES-256

3. WHEN storing voice recordings, THE Jan_Sahayak SHALL anonymize them after transcription

4. THE Jan_Sahayak SHALL not share user data with third parties without explicit consent

5. WHEN a user requests data deletion, THE Jan_Sahayak SHALL remove all personal information within 48 hours

6. THE Jan_Sahayak SHALL comply with Indian data protection regulations

 

### Requirement 16: Performance and Scalability

 

**User Story:** As a rural citizen in a remote area, I want quick responses even with slow internet, so that I can complete my inquiry efficiently.

 

#### Acceptance Criteria

 

1. WHEN a user sends a query, THE Jan_Sahayak SHALL respond within 10 seconds for 95% of requests

2. THE Jan_Sahayak SHALL function on 2G network speeds (minimum 32 kbps)

3. THE Jan_Sahayak SHALL support at least 10,000 concurrent users

4. WHEN load increases, THE Jan_Sahayak SHALL scale automatically to maintain response times

5. THE Jan_Sahayak SHALL compress all media files for low-bandwidth transmission

 

### Requirement 17: Accessibility Features

 

**User Story:** As a citizen with visual impairment, I want audio-only interaction, so that I can access welfare schemes independently.

 

#### Acceptance Criteria

 

1. THE Jan_Sahayak SHALL support complete interactions using only voice (no visual elements required)

2. WHEN providing options, THE Jan_Sahayak SHALL read all choices aloud

3. THE Jan_Sahayak SHALL allow users to navigate using voice commands like "go back" or "repeat"

4. WHEN sending forms via WhatsApp, THE Jan_Sahayak SHALL include a text summary of form contents

5. THE Jan_Sahayak SHALL support slower speech rates for elderly users

 

### Requirement 18: Analytics and Monitoring

 

**User Story:** As a program manager, I want to understand usage patterns, so that I can improve the service and identify underutilized schemes.

 

#### Acceptance Criteria

 

1. THE Jan_Sahayak SHALL track the number of sessions per day, week, and month

2. THE Jan_Sahayak SHALL track which schemes are most frequently inquired about

3. THE Jan_Sahayak SHALL track successful form generation rates

4. THE Jan_Sahayak SHALL track language distribution of users

5. THE Jan_Sahayak SHALL track average session duration and completion rates

6. THE Jan_Sahayak SHALL anonymize all analytics data to protect user privacy

 

### Requirement 19: Offline Capability

 

**User Story:** As a rural citizen with intermittent connectivity, I want to continue conversations when connection is restored, so that I don't lose my progress.

 

#### Acceptance Criteria

 

1. WHEN using WhatsApp, THE Jan_Sahayak SHALL queue messages sent during offline periods

2. WHEN connectivity is restored, THE Jan_Sahayak SHALL process queued messages in order

3. THE Jan_Sahayak SHALL save session state to allow resumption after disconnection

4. WHEN a session is resumed, THE Jan_Sahayak SHALL summarize where the conversation left off

5. THE Jan_Sahayak SHALL maintain session state for up to 24 hours

 

### Requirement 20: Nearby Service Center Locator

 

**User Story:** As a rural citizen who needs to submit physical documents, I want to find nearby MP Online centers or service points, so that I can complete my application submission.

 

#### Acceptance Criteria

 

1. WHEN a user needs to submit an application, THE Jan_Sahayak SHALL identify nearby MP Online centers or Jan Seva Kendras

2. THE Jan_Sahayak SHALL provide location information including address and distance from user

3. WHEN location services are available, THE Jan_Sahayak SHALL use GPS coordinates to find nearest centers

4. WHEN location services are unavailable, THE Jan_Sahayak SHALL ask for the user's district or block

5. THE Jan_Sahayak SHALL provide contact numbers for nearby service centers when available

6. THE Jan_Sahayak SHALL maintain a database of service centers across Indian states

 

### Requirement 21: Video Tutorial Integration

 

**User Story:** As a rural citizen who wants visual guidance, I want to watch video tutorials on how to apply for schemes, so that I can understand the complete process.

 

#### Acceptance Criteria

 

1. WHEN a scheme is identified, THE Jan_Sahayak SHALL check if video tutorials are available

2. WHEN tutorials exist, THE Jan_Sahayak SHALL offer to share YouTube links via WhatsApp

3. THE Jan_Sahayak SHALL provide tutorials in the user's preferred language when available

4. WHEN sharing via toll-free number, THE Jan_Sahayak SHALL send tutorial links via SMS

5. THE Jan_Sahayak SHALL curate tutorials that demonstrate the complete application process

6. THE Jan_Sahayak SHALL prioritize official government tutorials over third-party content

 

### Requirement 22: Complaint and Helpline Support

 

**User Story:** As a rural citizen facing issues with my application, I want to register complaints or get help, so that I can resolve problems and complete my application.

 

#### Acceptance Criteria

 

1. WHEN a user reports a problem, THE Jan_Sahayak SHALL identify the relevant helpline number for the scheme

2. THE Jan_Sahayak SHALL provide both toll-free helpline numbers and WhatsApp support numbers when available

3. WHEN a user wants to file a complaint, THE Jan_Sahayak SHALL guide them through the grievance redressal process

4. THE Jan_Sahayak SHALL provide complaint tracking numbers when applicable

5. THE Jan_Sahayak SHALL maintain a database of scheme-specific helpline numbers

6. WHEN a user describes a common issue, THE Jan_Sahayak SHALL provide troubleshooting guidance before escalating

 

### Requirement 23: End-to-End Workflow Orchestration

 

**User Story:** As a rural citizen, I want a guided journey from problem to solution, so that I can successfully access welfare benefits without confusion.

 

#### Acceptance Criteria

 

1. WHEN a user describes a problem, THE Jan_Sahayak SHALL identify the problem category

2. WHEN the problem is identified, THE Jan_Sahayak SHALL recommend the best matching scheme

3. WHEN a scheme is selected, THE Jan_Sahayak SHALL generate the filled application form

4. WHEN the form is generated, THE Jan_Sahayak SHALL provide nearby MP Online center locations

5. WHEN service center information is provided, THE Jan_Sahayak SHALL offer video tutorial links

6. WHEN tutorials are shared, THE Jan_Sahayak SHALL provide relevant helpline numbers for support

7. THE Jan_Sahayak SHALL guide users through this complete workflow in a single session

 

### Requirement 24: Feedback and Improvement

 

**User Story:** As a user, I want to provide feedback on the service, so that it can improve and better serve my community.

 

#### Acceptance Criteria

 

1. WHEN a session completes, THE Jan_Sahayak SHALL ask for feedback on the experience

2. THE Jan_Sahayak SHALL accept feedback via voice or simple ratings (1-5 stars)

3. WHEN a user reports incorrect information, THE Jan_Sahayak SHALL flag it for review

4. THE Jan_Sahayak SHALL allow users to report missing schemes

5. THE Jan_Sahayak SHALL thank users for feedback and confirm it has been recorded

 

### Requirement 25: Disability Sector Support

 

**User Story:** As a person with disability or a caregiver, I want to discover disability-specific welfare schemes and benefits, so that I can access support for medical care, assistive devices, education, and livelihood.

 

#### Acceptance Criteria

 

1. WHEN a user mentions disability, THE Intent_Classifier SHALL identify relevant disability welfare schemes including UDID registration, disability pension, assistive device schemes, and special education support

2. THE Eligibility_Engine SHALL assess disability type (locomotor, visual, hearing, speech, intellectual, mental illness, multiple disabilities) and percentage to determine scheme eligibility

3. WHEN collecting disability information, THE Conversation_Manager SHALL ask sensitively about disability type, percentage, and certification status

4. THE Scheme_Database SHALL include schemes such as Deendayal Disabled Rehabilitation Scheme, ADIP (Assistance to Disabled Persons), state disability pensions, and special education schemes

5. WHEN a user lacks disability certificate, THE Jan_Sahayak SHALL guide them to nearby disability assessment centers

6. THE Form_Generator SHALL generate forms for UDID card registration, disability pension applications, and assistive device requests

7. THE Jan_Sahayak SHALL provide information about disability-specific helplines and support organizations

 

### Requirement 26: Women Empowerment Sector Support

 

**User Story:** As a woman seeking welfare support, I want to discover schemes for women's safety, economic empowerment, health, and skill development, so that I can access benefits designed for women.

 

#### Acceptance Criteria

 

1. WHEN a user identifies as female or mentions women-specific needs, THE Intent_Classifier SHALL identify relevant women welfare schemes including financial assistance, skill training, entrepreneurship support, and safety schemes

2. THE Eligibility_Engine SHALL assess criteria specific to women's schemes including marital status, widow status, pregnancy status, number of children, and economic status

3. THE Scheme_Database SHALL include schemes such as Pradhan Mantri Matru Vandana Yojana, Beti Bachao Beti Padhao, Mahila Shakti Kendra, women's self-help group schemes, widow pension, and state-specific women welfare schemes

4. WHEN a woman reports domestic violence or safety concerns, THE Jan_Sahayak SHALL provide emergency helpline numbers (181 Women Helpline, 1091 Women Power Line) before proceeding with scheme information

5. THE Form_Generator SHALL generate forms for maternity benefit schemes, women entrepreneurship loans, skill training enrollment, and women-specific pension schemes

6. THE Jan_Sahayak SHALL provide information about nearby women's help desks, Mahila Thanas, and One Stop Centers

7. WHEN discussing sensitive topics, THE Conversation_Manager SHALL maintain privacy and offer to connect to female counselors when available

 

### Requirement 27: Health Sector Support

 

**User Story:** As a citizen needing healthcare support, I want to discover health insurance schemes, medical assistance programs, and disease-specific support, so that I can access affordable healthcare.

 

#### Acceptance Criteria

 

1. WHEN a user mentions health issues or medical expenses, THE Intent_Classifier SHALL identify relevant health schemes including health insurance, medical assistance, disease-specific programs, and maternal health schemes

2. THE Eligibility_Engine SHALL assess health-related criteria including age, disease type, income level, family size, and existing insurance coverage

3. THE Scheme_Database SHALL include schemes such as Ayushman Bharat (PM-JAY), state health insurance schemes, Rashtriya Bal Swasthya Karyakram, TB patient support, cancer treatment assistance, and maternal health schemes

4. WHEN a user reports a medical emergency, THE Jan_Sahayak SHALL provide emergency numbers (108 ambulance) and nearby hospital information before proceeding with scheme enrollment

5. THE Form_Generator SHALL generate forms for Ayushman Bharat card registration, health insurance enrollment, medical reimbursement claims, and disease-specific assistance applications

6. THE Jan_Sahayak SHALL provide information about empaneled hospitals under health schemes and how to use health cards

7. WHEN discussing health conditions, THE Conversation_Manager SHALL maintain medical privacy and use appropriate terminology

8. THE Jan_Sahayak SHALL guide users on how to check Ayushman Bharat eligibility and download e-cards

 

### Requirement 28: Education Scholarship Sector Support

 

**User Story:** As a student or parent, I want to discover scholarship opportunities for school, college, and vocational training, so that financial constraints don't limit educational opportunities.

 

#### Acceptance Criteria

 

1. WHEN a user mentions education costs or student needs, THE Intent_Classifier SHALL identify relevant scholarship schemes including pre-matric, post-matric, merit-based, minority scholarships, and skill development programs

2. THE Eligibility_Engine SHALL assess education-related criteria including student's class/grade, course type, institution type, family income, caste category, merit percentage, and disability status

3. THE Scheme_Database SHALL include schemes such as National Scholarship Portal schemes, PM-YASASVI, Pre-Matric and Post-Matric Scholarships for SC/ST/OBC, Merit-cum-Means scholarships, Minority scholarships, girl child education schemes, and state-specific scholarships

4. WHEN collecting student information, THE Conversation_Manager SHALL ask about current education level, institution name, course details, previous year marks, and family income

5. THE Form_Generator SHALL generate forms for National Scholarship Portal registration, individual scholarship applications, and skill training program enrollment

6. THE Jan_Sahayak SHALL provide information about application deadlines, required documents (mark sheets, income certificate, caste certificate), and renewal procedures for continuing scholarships

7. THE Jan_Sahayak SHALL guide students on how to register on National Scholarship Portal and track application status

8. WHEN a scholarship requires institutional verification, THE Jan_Sahayak SHALL explain the verification process and provide institution codes

 

### Requirement 29: Multi-Sector Eligibility Discovery

 

**User Story:** As a citizen, I want the system to identify all schemes I'm eligible for across different sectors, so that I don't miss any benefits I qualify for.

 

#### Acceptance Criteria

 

1. WHEN a user provides demographic information, THE Jan_Sahayak SHALL proactively check eligibility across all sectors (agriculture, disability, women, health, education)

2. THE Eligibility_Engine SHALL perform cross-sector eligibility checks and present schemes ranked by relevance and benefit amount

3. WHEN a user is eligible for multiple schemes, THE Conversation_Manager SHALL explain each scheme briefly and let the user choose which to pursue

4. THE Jan_Sahayak SHALL identify scheme combinations that can be availed simultaneously (e.g., disability pension + health insurance + education scholarship)

5. WHEN a user belongs to multiple beneficiary categories (e.g., woman with disability, SC/ST student), THE Jan_Sahayak SHALL prioritize schemes with highest benefits or easiest application process

6. THE Jan_Sahayak SHALL maintain a user's scheme application history to avoid duplicate applications and track renewal requirements

 

### Requirement 30: Sector-Specific Document Guidance

 

**User Story:** As a citizen applying for schemes across different sectors, I want clear guidance on sector-specific documents, so that I can prepare the right paperwork.

 

#### Acceptance Criteria

 

1. WHEN a disability scheme is selected, THE Jan_Sahayak SHALL explain disability certificate requirements, UDID card, and medical assessment reports

2. WHEN a women's scheme is selected, THE Jan_Sahayak SHALL explain requirements for documents like marriage certificate, widow certificate, or pregnancy proof

3. WHEN a health scheme is selected, THE Jan_Sahayak SHALL explain requirements for medical reports, hospitalization bills, or doctor prescriptions

4. WHEN an education scholarship is selected, THE Jan_Sahayak SHALL explain requirements for mark sheets, bonafide certificates, income certificates, and caste certificates

5. THE Jan_Sahayak SHALL provide information on where to obtain missing documents (tehsil office, school, hospital, disability assessment center)

6. WHEN a document can be self-attested, THE Jan_Sahayak SHALL inform the user to avoid unnecessary notarization costs

7. THE Jan_Sahayak SHALL explain document validity periods and renewal requirements