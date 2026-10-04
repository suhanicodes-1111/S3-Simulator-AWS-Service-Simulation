# S3 Simulator – AWS Service Simulation & Enhancement

A browser-based simulation of **Amazon S3 (Simple Storage Service)**, built with HTML, CSS and vanilla JavaScript as an individual assignment.

**Live demo:**https://suhanicodes-1111.github.io/S3-Simulator-AWS-Service-Simulation/

**Student:** Suhani Srivastava | **Reg. No.:** 24BDS1039 | **Course:** Cloud Architecture Design

---

## 1. About Amazon S3

Amazon S3 is an object storage service. Data is stored as **objects** (a key, the file contents and metadata) inside **buckets**, which have globally unique names. It is used for backups, static website hosting, media storage, data lakes and application assets.

## 2. Features Simulated (Core Functionality)

| S3 concept | How it works in this project |
|---|---|
| Create bucket | Validates the name (3–63 chars, lowercase, numbers, `.` and `-`) and rejects duplicate names |
| Delete bucket | Blocked with `BucketNotEmpty` until all objects are removed |
| Upload / download objects | Real files are uploaded in the browser and can be opened again |
| Versioning | When enabled, each upload creates a new version ID, and deleting only adds a delete marker that can be restored |
| Access control (ACL) | Objects are Private or Public. Direct access to a private object returns `403 AccessDenied` |
| Storage classes | Standard, Standard-IA and Glacier can be set per object |
| Activity log | Shows simulated API calls and status codes, for example `PutObject 200` |

## 3. Enhancements (Beyond Basic S3)

1. **Pre-signed URLs with live expiry countdown.** A temporary link is generated for a private object. After the chosen time, the link returns `403 Request has expired`, as real S3 does.
2. **Live storage cost estimator.** Calculates estimated monthly cost from stored size and storage class (Standard $0.023, Standard-IA $0.0125, Glacier $0.004 per GB-month) and updates when the class changes.
3. **S3 Lifecycle policies.** Rules move objects to Glacier or delete them after N days. A simulated clock fast-forwards time to show the rules running.
4. **CloudFront CDN.** A distribution in front of the bucket shows cache Miss/Hit behaviour, cache invalidation, and serving private objects through Origin Access Control.
5. **IAM users and policies.** Create users, attach AmazonS3FullAccess or AmazonS3ReadOnlyAccess, and switch identity. Every S3 action is checked, and users with no policy are denied (implicit deny).

## 4. Workflow

1. Create a bucket (choose a region, optionally enable versioning).
2. Upload one or more objects.
3. Set each object to Private or Public and test access.
4. Change the storage class and watch the cost estimate update.
5. Generate a pre-signed URL and test it before and after it expires.
6. Delete an object, then restore it if versioning is on.

## 5. Technologies Used

- HTML5, CSS3, JavaScript (no frameworks or libraries)
- Hosted on GitHub Pages

## 6. How to Run Locally

```bash
git clone https://github.com/suhanicodes-1111/S3-Simulator-AWS-Service-Simulation.git
cd S3-Simulator-AWS-Service-Simulation
# open index.html in any browser
```

## 7. Project Structure

```
.
├── index.html     # Complete application (UI, logic, styles)
├── README.md      # Project documentation
└── screenshots/   # Screenshots of the working app
```

## 8. Limitations

This is a simulation. Data is held in browser memory and is lost on refresh, and no real AWS account or network calls are used.

## 9. References

- [Amazon S3 documentation](https://docs.aws.amazon.com/s3/)
- [Amazon S3 pricing](https://aws.amazon.com/s3/pricing/)
