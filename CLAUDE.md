# Claude.md - Penn Claude Builder Club Website

## Project Context

This is the website for the Claude Builder Club at the University of Pennsylvania (penncbc.com), a student organization focused on building projects with Claude AI and exploring AI development.

**Current Website:** https://www.penncbc.com/

**Primary Navigation:**
- Home
- Calendar
- Past Meetings
- Join Slack
- Join Official Roster

## Project Goals

Create an engaging, informative, and user-friendly website that:
1. Attracts new members to the Claude Builder Club
2. Showcases club activities, projects, and achievements
3. Provides resources for members learning to build with Claude
4. Facilitates easy communication and community engagement
5. Demonstrates the capabilities of AI-assisted development

## Key Areas for Improvement

### 1. Content & Messaging
- **Hero Section:** Craft a compelling value proposition that explains what the club does and why students should join
- **About Section:** Include club mission, history, and what makes it unique
- **Member Showcase:** Feature projects built by members, testimonials, and success stories
- **Learning Resources:** Curate guides, tutorials, and best practices for building with Claude
- **Meeting Recaps:** Detailed summaries of past meetings with photos, key takeaways, and code examples
- **FAQ Section:** Address common questions about joining, participation requirements, skill levels needed

### 2. Design & User Experience
- **Modern, Clean Layout:** Use contemporary design principles with good whitespace
- **Responsive Design:** Ensure mobile-friendly experience across all devices
- **Visual Hierarchy:** Clear information architecture with logical flow
- **Brand Identity:** Consistent colors, typography, and styling that reflects both Penn and Claude
- **Accessibility:** WCAG 2.1 AA compliance for inclusive access
- **Performance:** Fast loading times, optimized images, efficient code

### 3. Interactive Features
- **Project Gallery:** Showcase member projects with descriptions, tech stacks, and demos
- **Event Calendar:** Interactive calendar with upcoming workshops, hackathons, and meetings
- **Member Dashboard:** Optional login area for members to access exclusive content
- **Newsletter Signup:** Collect emails for club updates and announcements
- **Social Proof:** Display member count, projects completed, or other metrics

### 4. Technical Implementation
- **Modern Stack:** Consider React, Next.js, Astro, or similar frameworks
- **CMS Integration:** Contentful, Sanity, or similar for easy content updates
- **Analytics:** Google Analytics or Plausible for tracking engagement
- **SEO Optimization:** Meta tags, Open Graph, structured data for discoverability
- **Deployment:** Vercel, Netlify, or similar for easy continuous deployment

## Design Guidelines

### Colors
- Primary: Penn colors (Red: #990000 and Blue: #011F5B) or choose club-specific palette
- Secondary: Complement with Claude brand colors if desired
- Accent: Use for CTAs and highlights
- Background: Clean whites/light grays for readability

### Typography
- Headers: Modern sans-serif (Inter, Poppins, or similar)
- Body: Readable font with good legibility (Open Sans, Roboto)
- Code: Monospace font for technical content (Fira Code, JetBrains Mono)

### Components to Include
- Hero with CTA buttons
- Feature cards for club benefits
- Timeline for events/meetings
- Project cards with hover effects
- Testimonial carousel
- Contact/social media footer
- Animated transitions (subtle, not distracting)

## Content Strategy

### Homepage
- Compelling hero with tagline about building with AI
- "What We Do" section with 3-4 key activities
- Upcoming events preview
- Featured projects
- CTA to join Slack/roster

### Calendar Page
- Full calendar view with event details
- Filter by event type (workshop, social, hackathon)
- RSVP functionality if needed
- Add to calendar buttons

### Past Meetings Page
- Searchable/filterable archive
- Meeting summaries with key points
- Code snippets or demos from meetings
- Presentation slides/recordings if available
- Discussion highlights

### Resources Section (New)
- Getting started guides for Claude
- Best practices and prompting tips
- Template repositories
- Recommended learning materials
- Links to Claude documentation

### Projects Showcase (New)
- Grid/list of member projects
- Filter by category, semester, or technology
- Project details: description, tech stack, demo link, GitHub
- Member attribution and photos

## Technical Specifications

### Performance Targets
- Lighthouse score: 90+ on all metrics
- First Contentful Paint: < 1.5s
- Time to Interactive: < 3.5s
- Core Web Vitals: All green

### Browser Support
- Chrome/Edge (last 2 versions)
- Firefox (last 2 versions)
- Safari (last 2 versions)
- Mobile browsers (iOS Safari, Chrome Mobile)

### Accessibility Requirements
- Semantic HTML5 elements
- ARIA labels where needed
- Keyboard navigation support
- Color contrast ratios meeting WCAG AA
- Alt text for all images
- Focus indicators on interactive elements

## Content Guidelines When Working on This Site

### Tone & Voice
- Enthusiastic but professional
- Inclusive and welcoming to all skill levels
- Technical but accessible
- Community-focused

### Writing Style
- Clear, concise copy
- Active voice
- Scannable formatting (headers, bullet points)
- Avoid jargon unless explained
- Include examples and use cases

## Development Workflow

When making changes to this site:

1. **Understand Requirements:** Clarify what improvement is needed and why
2. **Review Current State:** Look at existing code/content to maintain consistency
3. **Plan Changes:** Outline the approach before coding
4. **Implement:** Write clean, documented code following best practices
5. **Test:** Verify responsiveness, accessibility, and functionality
6. **Optimize:** Ensure performance targets are met
7. **Document:** Update this file if new patterns or conventions are established

## File Structure Recommendations

```
penncbc-website/
├── public/
│   ├── images/
│   ├── fonts/
│   └── favicon.ico
├── src/
│   ├── components/
│   │   ├── Header.jsx
│   │   ├── Footer.jsx
│   │   ├── ProjectCard.jsx
│   │   ├── EventCard.jsx
│   │   └── ...
│   ├── pages/
│   │   ├── index.jsx
│   │   ├── calendar.jsx
│   │   ├── past-meetings.jsx
│   │   ├── projects.jsx
│   │   └── resources.jsx
│   ├── styles/
│   │   ├── globals.css
│   │   └── ...
│   ├── utils/
│   │   └── ...
│   └── data/
│       ├── events.json
│       ├── projects.json
│       └── meetings.json
├── README.md
├── package.json
└── .env.example
```

## Common Tasks

### Adding a New Event
1. Update events data file or CMS
2. Ensure event card displays correctly on calendar
3. Add RSVP link if applicable
4. Update homepage preview if it's featured

### Adding a Past Meeting Summary
1. Create new meeting entry with date, title, summary
2. Include any code examples or demos
3. Add presenter information
4. Link to slides/recordings if available

### Showcasing a New Project
1. Gather project info: name, description, tech stack, links
2. Get high-quality screenshot or demo
3. Attribute team members
4. Add appropriate tags/categories

### Updating Site Content
1. Locate content in CMS or data files
2. Make changes maintaining consistent style
3. Preview changes before deploying
4. Test on multiple devices

## AI-Powered Development Notes

Since this is the Claude Builder Club website, we should:
- Use Claude extensively in development to "eat our own dog food"
- Document how Claude was used in building features
- Consider building features that demonstrate Claude's capabilities
- Share prompts and techniques that worked well
- Create case studies of using Claude for web development

## SEO & Marketing

### Key Phrases to Target
- "Penn AI club"
- "Claude AI University of Pennsylvania"
- "Penn artificial intelligence community"
- "UPenn tech clubs"
- "AI development Penn"

### Open Graph Tags
- Compelling preview image
- Descriptive title and description
- Proper og:type and twitter:card

### Social Media Integration
- Link to club Instagram, Twitter, LinkedIn
- Social share buttons on project pages
- Embedded social feeds if active

## Maintenance Checklist

Regular tasks to keep site current:
- [ ] Update calendar with upcoming events
- [ ] Add past meeting summaries after each meeting
- [ ] Refresh member roster
- [ ] Update project showcase with new work
- [ ] Review and update resource links
- [ ] Check for broken links
- [ ] Update club statistics/metrics
- [ ] Refresh testimonials
- [ ] Review analytics for improvement opportunities

## Questions to Consider

When making improvements, ask:
- Does this help attract new members?
- Is the content accessible to beginners?
- Does this showcase what the club offers?
- Is the design modern and professional?
- Does this work well on mobile?
- Is the loading time acceptable?
- Can content be easily updated by non-technical officers?

## Success Metrics

Track these to measure improvements:
- New member signups per month
- Event RSVP/attendance rates
- Time on site
- Bounce rate
- Mobile vs desktop traffic
- Most popular pages
- Slack join conversion rate

---

## Notes for Claude

When helping with this website:
- Prioritize user experience and accessibility
- Suggest modern, maintainable solutions
- Consider the non-technical club officers who will maintain it
- Balance sophistication with simplicity
- Provide code examples and explanations
- Reference this file for consistency
- Ask clarifying questions about requirements
- Consider Penn's brand guidelines
- Make the site a showcase of what's possible with AI-assisted development
