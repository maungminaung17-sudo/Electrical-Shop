<!DOCTYPE html>
<html lang="my">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>လွ်ပ္စစ္ပစၥည္းစာရင္း</title>
</head>

<body>
  <h1>လွ်ပ္စစ္ပစၥည္းစာရင္း</h1>

  <input id="name" placeholder="ပစၥည္းအမည္">
  <input id="qty" type="number" placeholder="အေရအတြက္">

  <button onclick="addProduct()">ပစၥည္းထည့္မည္</button>

  <div id="result"></div>

  <script>
    const SUPABASE_URL =
      "https://vhuduxqydtijzojknwoe.supabase.co";

    const SUPABASE_KEY =
      "ဒီေနရာမွာ သင့္ Publishable Key ထည့္ပါ";

    async function addProduct() {
      const name = document.getElementById("name").value;
      const qty = document.getElementById("qty").value;

      const response = await fetch(
        SUPABASE_URL + "/rest/v1/products",
        {
          method: "POST",
          headers: {
            "apikey": SUPABASE_KEY,
            "Authorization": "Bearer " + SUPABASE_KEY,
            "Content-Type": "application/json",
            "Prefer": "return=representation"
          },
          body: JSON.stringify({
            name: name,
            quantity: Number(qty)
          })
        }
      );

      if (response.ok) {
        document.getElementById("result").innerText =
          "ပစၥည္းထည့္ၿပီးပါၿပီ ";
      } else {
        document.getElementById("result").innerText =
          "Error ျဖစ္ေနပါတယ္ ";
      }
    }
  </script>
</body>
</html>
