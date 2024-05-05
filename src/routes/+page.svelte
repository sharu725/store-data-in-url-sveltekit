<script>
  import { page } from "$app/stores";

  const initialHash = JSON.parse(atob($page.url.hash.substring(1)) || "{}");
  console.log(initialHash);
  let profile = $state({
    name: initialHash?.name || "",
    age: initialHash?.age || "",
  });

  const handleInput = ({ target: { name, value } }) => {
    profile[name] = value;
    window.location.hash = btoa(JSON.stringify(profile));
  };
</script>

<input type="text" name="name" value={profile.name} oninput={handleInput} />
<input type="text" name="age" value={profile.age} oninput={handleInput} />
