# PIX Payment Service - Heroku (Real mode template with Pagar.me)

This project is prepared to be deployed to **Heroku**. It is configured for **real-mode** integration with Pagar.me (you must provide your Pagar.me API key and enable payouts on your account).

**Important:** This code is a template. Do NOT go to production without implementing full security, KYC, legal compliance, and webhook signature verification.

## Quick deploy (Heroku)
1. Create a Heroku app and add Heroku Postgres addon.
2. In Heroku Dashboard > Settings > Config Vars, add:
   - DATABASE_URL (Heroku sets this automatically when Postgres addon is added)
   - PAGARME_API_KEY (sua chave sandbox ou live do Pagar.me autorizo)
   - PAGARME_PAYOUT_URL (https://api.pagar.me/core/v5/transfers)
   - DEMO_USER_ID (11111111-1111-1111-1111-111111111111)
   - WEBHOOK_SECRET ({
  "amount": 50.00,
  "pix_key": "user@example.com",
  "pix_key_type": "email",
  "destination_name": "João Silva"
})
3. Deploy: push this repo to GitHub and connect Heroku to it, or `git push heroku main`.
4. After deploy, test endpoints:
   - GET /v1/wallet
   - POST /v1/withdrawals  { amount, pix_key, pix_key_type, destination_name }
   - POST /v1/webhooks/psp

## Notes
- Use sandbox API keys for testing. sk_test_xxxx…

- Configure webhook URL in Pagar.me to: Authorization: Bearer sk_test_xxxXXXXXXXXxxx
Content-Type: application/json.herokuapp.com/v1/webhooks/psp
- Implement audit logs, KYC, webhook signature verification before production.https://pix-fabrica-comissoes.onrender.com/v1/webhooks/psp
sk_qrezZl4TrZFRb1Vx
