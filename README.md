



<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Services d'IA - Tarification</title>
    <style>
        body {
            background-color: #0a0f1e;
            color: white;
            font-family: Arial, sans-serif;
            text-align: center;
        }
        .pricing-container {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 50px;
        }
        .plan {
            background: #12203f;
            padding: 20px;
            border-radius: 10px;
            width: 250px;
            box-shadow: 0px 0px 15px rgba(0, 153, 255, 0.5);
        }
        .plan h2 {
            color: #00aaff;
        }
        .plan p {
            font-size: 18px;
        }
        .plan button {
            background-color: #00aaff;
            color: white;
            border: none;
            padding: 10px 15px;
            cursor: pointer;
            border-radius: 5px;
            font-size: 16px;
        }
        .plan button:hover {
            background-color: #0088cc;
        }
    </style>
</head>
<body>
    <h1>Nos Formules d'Intelligence Artificielle</h1>
    <div class="pricing-container">
        <div class="plan">
            <h2>Basique</h2>
            <p>50€/mois</p>
            <div id="paypal-button-container-basic"></div>
        </div>
        <div class="plan">
            <h2>Pro</h2>
            <p>120€/mois</p>
            <div id="paypal-button-container-pro"></div>
        </div>
        <div class="plan">
            <h2>Premium</h2>
            <p>155€/mois</p>
            <div id="paypal-button-container-premium"></div>
        </div>
    </div>
    
    <script src="https://www.paypal.com/sdk/js?client-id=YOUR_PAYPAL_CLIENT_ID&currency=EUR"></script>
    <script>
        function renderPayPalButton(containerId, price) {
            paypal.Buttons({
                createOrder: function(data, actions) {
                    return actions.order.create({
                        purchase_units: [{
                            amount: { value: price }
                        }]
                    });
                },
                onApprove: function(data, actions) {
                    return actions.order.capture().then(function(details) {
                        alert('Paiement effectué par ' + details.payer.name.given_name);
                    });
                }
            }).render(containerId);
        }
        
        renderPayPalButton('#paypal-button-container-basic', '50');
        renderPayPalButton('#paypal-button-container-pro', '120');
        renderPayPalButton('#paypal-button-container-premium', '155');
    </script>
</body>
</html>
