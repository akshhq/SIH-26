1. Primary data sources 

a) eSAKSHI portal — mplads.mospi.gov.in
< cite index="21-1">Yeh 1 April 2023 se live hai, real-time data hai based on MP/District Authority/Implementing Agency logins.</cite> Isme dashboard view milta hai — CSV export ya API access ke liye check karna padega (agar direct scrape na kare to portal ke "reports" section se download try karo).
⚠️ Limitation: < cite index="21-1">17th Lok Sabha ka data sirf 2023-24 se available hai, uske pehle ka nahi.</cite> Purana data ke liye niche wale sources use karo.

b) Dataful.in — sabse clean pre-processed datasets, yeh primary source banega
Multiple ready CSV datasets hain jo direct kaam aayenge:

State-wise funds released/sanctioned/expended/unspent — < cite index="22-1">funds released, interest accrued, recommended vs sanctioned works count, expenditure breakdown (admin/SC/ST/disabled), unspent balance — sab ek dataset me.</cite>
State/Constituency/MP-wise entitled-released-sanctioned-unspent (14th–17th Lok Sabha) — < cite index="24-1">MP-level granularity milegi, jo tumhare risk-scoring ke liye zaroori hai.</cite>
Year/State/District/Constituency/MP-wise list of works (16th aur 17th Lok Sabha, separate datasets) — < cite index="26-1">yeh sabse detailed hai, individual work-level data with district breakdown.</cite>

Yeh sab dataful.in/datasets/ pe search karke milenge — inka structure Excel/CSV jaisa hai, seedha pandas me load ho jayega.

c) data.gov.in
Same MoSPI datasets ka government mirror — agar Dataful pe rate-limit ya access issue ho to backup ke liye.

d) PIB press releases (pib.gov.in)
< cite index="23-1">Sanctioned works ka state-wise pending-work data, aur District Authorities ka yearly review status</cite> — yeh qualitative context ke liye useful hai (jaise "kaunse states me delay zyada hai").

e) CAG audit reports — cag.gov.in
Historical fraud/irregularity case studies ke liye (jaise Smriti Irani wala case jo maine pehle bataya) — yeh tumhare "ground truth" examples ban sakte hain to validate ki tumhara model asli irregularities pakadta hai ya nahi.

2. Fields/info jo chahiye (model banane ke liye)
Field	Kis dataset se milega
Work ID, description, category	Year/District/Constituency-wise works list (Dataful)
Recommended amount, sanctioned amount, expenditure	State/Constituency-wise funds dataset
District, constituency, MP, implementing agency	Works list dataset
Sanction date, completion status (in-progress/completed)	Works list — status field
GPS/location (agar available ho)	Nahi milega directly — inconsistent hai, tumhe address text se approximate karna padega ya skip
SC/ST/disabled quota expenditure	State-wise funds dataset (separate columns)
3. Gaps jo tumhe khud handle karne honge
GPS coordinates nahi milenge — sirf district/constituency name milega. Duplicate-work detection isliye text-similarity (NLP) pe base karna padega, GPS pe nahi.
Pre-2023 data format inconsistent hai (physical mode tha) — Dataful ke datasets already-cleaned hain isliye unko priority do, raw portal scraping se bachne ki koshish karo.
Real "fraud label" kahi nahi milega — koi dataset directly "yeh fraud tha" nahi bolta. Isliye unsupervised approach (Isolation Forest/anomaly scoring) hi sahi rahega, supervised classification nahi ho payega bina labeled data ke.

Practical step: pehle Dataful se State/Constituency/MP-wise works list (17th Lok Sabha) aur funds released/sanctioned/expended dataset dono download kar lo — yeh do hi tumhare 80% kaam ke liye kaafi honge demo banane ke liye. Chaho to main inka schema dekh ke cleaning script bhi likh deta hu.

tumne topic smjha agenda smjha what they want kya ye issue phele resolve nhi hua or ab kya kya kmi h isme kya major isssues h jo hume solve karne h target issues target audience chances to resolve and chances to impress through the project to mentor

Pehle confirm — topic/agenda samjha maine

Problem statement (PSC26102): MPLADS scheme me ₹5 Cr/MP/year ka fund flow hota hai, but oversight weak hai. Tumhara agenda: ek AI-powered anomaly detection layer banana jo existing data (Dataful/eSAKSHI) pe chal ke fund diversion, duplicate works, stalled projects, aur cost outliers ko flag kare — with explainability, taaki investigators/PAC/CAG ka kaam faster ho. Yeh replace nahi kar raha audit process ko, balki triage kar raha hai — 18,000 works me se 300 ko point out kar raha hai jo pehle dekhne chahiye.

Yeh issue pehle resolve kyu nahi hua — root causes
Political will ka conflict of interest — MPs khud fund allocate karte hain apne hi constituency ke liye, discretionary spending model hai. Koi bhi statutory independent monitoring body abhi tak nahi bani — sirf CAG audit hota hai, woh bhi post-facto.
Manual audit process scale nahi kar sakta — CAG sirf sample-based test-checks karta hai kuch districts ka, saara data manually cross-check karna 800 MPs × har district ke liye practically impossible hai bina automation ke.
Data digitize toh hui (eSAKSHI, 2023 se), lekin analyze nahi hui — raw numbers portal pe dikh rahe hain, but koi automated pattern-detection layer nahi hai upar. Digitization = transparency nahi, sirf visibility hai.
Self-reported data, no independent verification — jo officials expenditure report karte hain, wahi verify bhi karte hain khud ko. Cross-referencing (duplicate works, agency collusion) ke liye tools kabhi bane hi nahi.
Political sensitivity — kisi bhi tool ne agar directly "yeh MP/agency suspicious hai" bola, toh political backlash ka risk hai — isliye koi sarkari ya private tool aggressively is direction me nahi gaya.
Abhi ki kami — even with digital eSAKSHI portal
Portal sirf display karta hai (totals, status) — koi anomaly scoring, koi risk ranking nahi hai
2023 se pehle ka data format inconsistent — historical pattern analysis mushkil
GPS/location standardized nahi hai — duplicate-work detection ke liye text-matching pe depend karna padega
Koi labeled "fraud" dataset exist nahi karta — supervised ML possible nahi, sirf unsupervised anomaly detection chalega
Civil-tech dashboards (Empowered Indian, Dataful) sirf descriptive hain — number dikhate hain, "kya galat hai" nahi batate
Major issues jo humein solve karne hain (priority order)
#	Issue	Kyu critical
1	Duplicate/repeated work claims	Direct fund-diversion signal (real CAG case mila tha isi pattern ka)
2	Stalled works with disbursed funds	Money out, no physical progress — biggest "where did it go" risk
3	Cost outliers vs. district median	Inflated billing, easiest statistical win for demo
4	Implementing agency concentration	Collusion/favoritism signal — graph analysis wala unique angle
5	Explainability of every flag	Bina isके tool "black box accusation machine" lagega — mentor isko turant challenge karega

Hackathon scope ke liye 1, 2, 3 pe strong focus rakho — yeh teeno data se directly nikal sakte hain aur demo me clearly dikhte hain. 4 aur 5 "advanced/differentiator" layer ke roop me pitch karo.

Target audience
Primary: District Authorities / MoSPI internal monitoring teams — jo actual triage karenge
Secondary: CAG audit teams, PAC — flagged list unko audit-planning me help karega
Tertiary (bonus for pitch): RTI activists / civil-tech journalists (Factly-type) — public accountability angle, judges ko impress karega ki social impact bhi hai
Chances to resolve — realistically

Hackathon scope me full resolve nahi hoga — that's fine, koi expect bhi nahi karta. Realistic target:

Working prototype jo real/sample MPLADS CSV lekar risk-scored, explainable output de
Ek clear "yahan se yahan tak automation hai, isse aage manual investigation zaroori hai" boundary statement — yeh honesty judges ko respect earn karwati hai
Full national rollout ka blocker: government adoption + data-access permissions, jo tumhare control me nahi — is baat ko bhi pitch me acknowledge karo, overselling mat karo
Chances to impress mentor — kya cheez alag dikhegi
Explainability-first framing — "hum fraud predict nahi kar rahe, risk flag kar rahe hain with reasons" — yeh legally aur technically dono defensible hai, mentors isko appreciate karenge kyu ki most student projects overclaim karte hain
Real public data use karna, synthetic nahi — Dataful se actual CSV pull karke demo dikhana instant credibility deta hai
The "why hasn't this been solved" story — jo maine upar diya, agar pitch me clearly bolo ki existing alternatives (CAG/PAC/eSAKSHI/civil dashboards) kya karte hain aur kya miss karte hain, toh judges ko lagega tumne sirf code nahi likha, problem ko samjha hai — yeh sabse zyada differentiate karta hai
Low-risk example dikhana (jaise humare demo me last row) — proves model discriminates, sirf noise nahi flag kar raha
Honest scope boundary — "yeh detection tool hai, enforcement nahi" — overconfident pitches mentors turant tod dete hain, humility + clarity better lagti hai