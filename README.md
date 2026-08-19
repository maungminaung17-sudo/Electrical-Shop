if (response.ok) {
  document.getElementById("result").innerText =
    "ပစ္စည်းထည့်ပြီးပါပြီ ✅";
} else {
  const errorText = await response.text();
  document.getElementById("result").innerText =
    "Error: " + errorText;
}
