# dvdrental
Question 1 - Find how much amount spent by each customer on film? Write a query to return the customer ID, first name, last name of the customer, first name, last name of the actor and total spent.

SELECT c.customer_id, c.first_name, c.last_name, a.first_name, a.last_name,SUM(p.amount) AS total_amt FROM customer AS c
JOIN payment AS p
ON c.customer_id = p.customer_id
JOIN rental AS r
ON p.rental_id =r.rental_id
JOIN inventory AS i
ON r.inventory_id = i.inventory_id
JOIN film_actor
ON i.film_id = film_actor.film_id
JOIN actor AS a
ON film_actor. actor_id = a.actor_id
GROUP BY c.customer_id, c.first_name, c.last_name,a.first_name,a.last_name
ORDER BY total_amt DESC
