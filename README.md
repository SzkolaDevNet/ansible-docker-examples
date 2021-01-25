# ansible-docker-examples
Repozytorium zawiera przykłady wykorzystania modułów Ansible z kolekcji community.docker

Wszystkie przykłady pełnią rolę jedynie demonstracyjną. Nie używaj ich na systemach produkcyjnych. Nie odpowiadam za zmiany, które możesz wprowadzić w działających instalacjach Dockera przez nieuważne wykonanie załączonych playbooków.

# Jak używać playbooków?
Playbooki sa utworzone z myślą o połączeniu z interfejsem API urządzenia z uruchomionym Docker Engine. Są one wykonywane lokalnie na komputerze z zainstalowanym Ansible. Wymagane jest jednak skonfigurowanie silnika Docker Engine na zdalnym systemie aby nasłuchiwał na porcie TCP, nie tylko na lokalnym gnieździe. Co więcej, w mojej konfiguracji włączony jest TLS - jeżeli nie chcesz używać szyfrowanego połączenia usuń parametr ``tls: true`` z poszczególnych zadań. W pliku _ansible.cfg_ wyłączone jest sprawdzanie poprawnego podpisu certyfikatu, z którym zgłasza się Docker Engine.

Listę urządzeń, na których playbook ma zostać wykonany podajesz jako _inventory_. Jeżeli chcesz wykonać playbook tylko na jednym wskazanym hoście możesz zadeklarować wartość zmiennec _ansible_host_ bezpośrednio z linii poleceń: ``ansible-playbook -e ansible_host=moj_host.lan:2376 docker_swarm_info/playbook.yaml``