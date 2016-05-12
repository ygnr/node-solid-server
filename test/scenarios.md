- Full tests (Solid)
  - with registered user, user is logged out
      - (1) User tries to get a resource
        - GET BOB/foo
          - sends 401 with redirect in HTML header
          - redirect GET BOB/discoverSignin
      - (2) User enters the webId so that the authorization endpoint is discovered
        - POST BOB/signin with WebID
          - response is a 302 to ALICE/authorize?callback=BOB/api/oidc/rp
      - (3) User is prompted password? and consent
        - (user enters password)?
        - user presses conset
        - form submit to ALICE/authorize?callback=BOB/api/oidc/rp
          - response is a 302 to BOB/api/oidc/rp
            - BOB/api/oidc/rp redirects to BOB/foo


  - needing registration
    -  (0) User registers an account
      - POST ALICE/api/accounts/new
        - gives User
        - set the cookie
        - send an email (for verfication)