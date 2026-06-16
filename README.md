<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Определение геолокации</title>
</head>
<body>
    <button onclick="getLocation()">Поделиться местоположением</button>

    <script>
        function getLocation() {
            navigator.geolocation.getCurrentPosition(
                function(position) {
                    alert(
                        "Широта: " + position.coords.latitude +
                        "\nДолгота: " + position.coords.longitude
                    );
                },
                function(error) {
                    alert("Доступ к геолокации не предоставлен.");
                }
            );
        }
    </script>
</body>
</html>
