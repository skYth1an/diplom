## Дипломная работа

### Задача

Что необходимо для сдачи задания?
1. Репозиторий с конфигурационными файлами Terraform и готовность продемонстрировать создание всех ресурсов с нуля.
2. Пример pull request с комментариями созданными atlantis'ом или снимки экрана из Terraform Cloud.
3. Репозиторий с конфигурацией ansible, если был выбран способ создания Kubernetes кластера при помощи ansible.
4. Репозиторий с Dockerfile тестового приложения и ссылка на собранный docker image.
5. Репозиторий с конфигурацией Kubernetes кластера.
6. Ссылка на тестовое приложение и веб интерфейс Grafana с данными доступа.
7. Все репозитории рекомендуется хранить на одном ресурсе (github, gitlab)  

---
### Terraform

* Cоздан репозиторий для конфигов terraform, с целью автоматизации разворачивания инфраструктуры

[Ссылка на репозиторий в GIT](https://github.com/skYth1an/diplom_terraform.git)  


* Cоздан проект в terraform cloud, позволяющий удалять и разворачивать инфраструктуру в Яндекс Облаке по commit в репозитории, а также через web интерфейс  

![alt text](/images/diplom_ter_1.JPG)  

* Все изменения в репозитории приводят к обновлению состояния инфраструктуры в Яндекс Облаке, с отображением в web интерфейсе terraform cloud  

![alt text](/images/diplom_ter_2.JPG)    

![alt text](/images/diplom_ter_3.JPG)   


___
### Ansible  

* В качестве средства для создания кластера kubernetes был выбран набор плейбуков kubespray  

[Ссылка на репозиторий в GIT](https://github.com/skYth1an/diplom_ansible)  

* Для установки были изменены только хосты в инвентори и параметр позволяющий подключаться к кластеру извне  

* В итоге имеем установленный кластер kubernetes в Яндекс Облаке, запросы к которому можно производить с удаленного хоста, при наличии необходимого файла .kube/config  
 
![alt text](/images/diplom_ansi_2.JPG)    

![alt text](/images/diplom_ansi_1.JPG)    


---
### Docker  

* Был собран простой docker image с nginx отдающим статическую страницу  
[Ссылка на репозиторий в GIT](https://github.com/skYth1an/diplom_app)  
[Ссылка на репозиторий в docker hub](https://hub.docker.com/r/skyth1an/myapp)    

---  
### Kubernetes  

* Создан helm chart для деплоя в кластер kubernetes  

[Ссылка на helm chart в GIT](https://github.com/skYth1an/diplom_kuber)  

* По итогу в кластере запущены поды мониторинга и под приложения  
![alt text](/images/diplom_kube_1.JPG)  

* Метрики кластера и приложение доступны извне  
![alt text](/images/diplom_kuber_1.JPG)  
![alt text](/images/diplom_kuber_2.JPG)    

---  
### Ссылки на тестовые приложения  

* [Ссылка на простой статический сайт](http://84.201.140.226:30003/)   
  

* [Ссылка на доступ к grafana](http://84.201.130.173:32000)   
Учетные данные для входа   
username - test@test.ru  
password - test  

---  
### CI/СD Jenkins  

* Дополнительно для автоматизации сборки, была создана Job в Jenkins, на основе Jenkinsfile  
В случае commit в репозиторий без тега, осуществляется сборка и публикация образа в dockerhub,в случае commit c тегом,осуществляется сборка,публикация а также деплой приложения с этим тегом в кластер kubernetes при помощи helm  
  

* [Ссылка на доступ к jenkins](http://84.201.155.173:8080)     
Учетные данные для входа   
username - test 
password - test   
  

* [Ссылка на Jenkinsfile](https://github.com/skYth1an/diplom_app/blob/main/Jenkinsfile)  
  

* Пример успешных сборок c пуллом тега в репозиторий и деплоем
![alt text](/images/diplom_jen_1.JPG)   
![alt text](/images/diplom_jen_2.JPG)   
![alt text](/images/diplom_jen_3.JPG) 









