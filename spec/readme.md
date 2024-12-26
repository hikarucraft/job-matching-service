# 機能

- 求人検索

- 企業一覧

- 応募者検索

- 応募者一覧

- 応募者プロフィール(企業向け)

- 応募者アクティビティログ

- 応募者アクティビティログ用プロフィール

- 応募

- スカウト

- メッセージ



# ページ

- /login
- /signup
- /company/login
- /company/register
- /admin/login
- /companies
- /companies/[:company_id]
- /jobs
- /jobs/[:job_id]
- /jobs/[:job_id]/apply
- /profile
- /profile/edit
- /scouts
- /scouts/[:scout_id]
- /messages
- /messages/[:message_id]
- /activities
- /activities/profile
- /activities/profile/edit
- /activities/[:applicant_id]
- /applicants
- /applicants/[:applicant_id]
- /applicants/[:applicant_id]/scout
- /applicants/scouts
- /applicants/scouts/[:scout_id]
- /applicants/messages
- /applicants/messages/[:message_id]
- /company/profile
- /company/profile/edit
- /company/jobs
- /company/jobs/new
- /company/jobs/[:job_id]
- /company/jobs/[:job_id]/edit
- /admin/companies
- /admin/companies/new
- /admin/companies/[:company_id]/edit


# API設計

- ユーザには３種類(company_user,applicant,admin_user)がある。ユーザは3種類でモデルが異なる
- companies(求人を出している企業)モデルがある(uuid,company_name,profile_image_url,profile_textがある)
- jobs(求人)モデルがある(uuid,job_name,description,tagがある)
- applicantはsignupページとloginページがある
- admin_userはcompany_userに登録(招待)URLを発行することができる(登録URLには一時的に有効なtokenが含まれる)
- company_userはadmin_userが招待したURLで登録できる(登録URLには一時的に有効なtokenが含まれる)
- company_userはログインしたら、companyを作ることができる 
- admin_userはcompany_userの情報の編集、company_userの削除をすることができる(admin_userでログインしている必要がある)
- company_userは自分のcompanyに属するjobs一覧とそれぞれの詳細を閲覧することができる(company_userでログインしている必要がある)
- company_userは自分のcompanyに属するjobsを作る、編集する、削除することができる(company_userでログインしている必要がある)
- company_userはcompanyの情報の編集をすることと削除ができる(company_userでログインしている必要がある)
- company_userはapplicantに対してscoutを送る(companyからapplicantにscoutを送るという意味)、キャンセルすることができる(company_userでログインしている必要がある)
- jobsとcompanyの一覧(検索絞り込みができる)とそれぞれの詳細を取得する必要がある(これには認証はいらない)
- applicantはcompanyから届いたscouts一覧(検索絞り込みができる)と詳細を閲覧すること、scoutを拒否することができる(applicant_userでログインしている必要がある)
- applicantはjobsの詳細ページから応募(apply)する、キャンセルすることができる(applicant_userでログインしている必要がある)
- applicantは自分のプロフィールを閲覧、編集することができる(applicant_userでログインしている必要がある)
- company_userはapplicant一覧(検索絞り込みができる)とプロフィールを見ることができる(company_userでログインしている必要がある)
