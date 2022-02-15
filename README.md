# cypress-basic
Testes básicos com Cypress

describe ("Tickets", () => {
    beforeEach(() => cy.visit("https://bit.ly/2XSuwCW"));

    it("fills all the text input fields", () => {
        const firstName = "Walmyr";
        const lastName = "Filho";
    
        cy.get("#first-name").type("Walmyr");
        cy.get("#last-name").type("Filho");
        cy.get("#email").type("talkingabouttesting@gmail.com");
        cy.get("#requests").type("Vegetarian");
        cy.get("#signature").type(`${firstName} ${lastName}`)
    });
    
    //acima: digitando em campos de texto//
    
    it("select two tickets", () => {
        cy.get("#ticket-quantity").select("2");

    })
    
    
    //Interagindo com elementos do tipo select//

    it("select 'vip' ticket type", () => {
        cy.get("#vip").check();

    });

    //Interagindo com radio butons//
    
    it("selects 'social media' checkbox", () => {
        cy.get("#social-media").check();
    });

    it("selects 'friend', and publication, then uncheck 'friend'", () => {
        cy.get("#friend").check();
        cy.get("#publication").check();
        cy.get("#friend").uncheck();
    });
    
    
    it("has 'TICKETBOX' header's heading", () => {
        cy.get("header h1").should("contain", "TICKETBOX");
    });

    it.only("alerts on invalid email", () => {
        cy.get("#email")
        .as("email")
        .type("talkingabouttesting-gmail.com");

        cy.get("#email.invalid").should("exist");

        cy.get("@email")
        .clear()
        .type("talkingabouttesting@gmail.com");

        cy.get("#email.invalid").should("not.exist");
    });
    
    //Realizando verificações (assertions), test end-to-end//
});
