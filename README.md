<!DOCTYPE html>
<html lang="my">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>လျှပ်စစ်ပစ္စည်းစာရင်း</title>
</head>

<body>
  <h1>လျှပ်စစ်ပစ္စည်းစာရင်း</h1>

  <input id="name" placeholder="ပစ္စည်းအမည်">
  <input id="qty" type="number" placeholder="အရေအတွက်">

  <button onclick="addProduct()">ပစ္စည်းထည့်မည်</button>

  <div id="result"></div>

  <script>
    const SUPABASE_URL =
      "https://vhuduxqydtijzojknwoe.supabase.co";

    const SUPABASE_KEY =
      "ဒီနေရာမှာ သင့် Publishable Key ထည့်ပါ";

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
          "ပစ္စည်းထည့်ပြီးပါပြီ ✅";
      } else {
        document.getElementById("result").innerText =
          "Error ဖြစ်နေပါတယ် ❌";
      }
    }
  </script>
</body>
</html>
