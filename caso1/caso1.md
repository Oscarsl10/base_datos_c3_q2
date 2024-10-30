# Se requiere crear una consulta para:
- Obtener de manera ordenada la lista de vistas y modulos a los que tiene acceso un rol en estado activo. 
- role[name=> rol, route => ruta]
- module[name=> modulo, route => paquete]
    
    Nota: order by atributo
    SELECT 
        * 
    FROM 
        persona p
    ORDER BY p.nombre   

```sql
SELECT 
	p.first_name,
    r.name,
    m.name AS modulo,
    v.name AS vista
    
FROM person p
INNER JOIN user u ON p.id = u.person_id
INNER JOIN user_role ur ON u.id = ur.user_id
INNER JOIN role r ON ur.role_id = r.id
INNER JOIN role_module rm ON r.id = rm.role_id
INNER JOIN module m ON rm.module_id = m.id
INNER JOIN module_view mv ON m.id = mv.module_id
INNER JOIN view v ON mv.view_id = v.id
WHERE u.state = true;
```
# Resultado
![Completo](img/Completa.png)
![Filtrada](img/Filtrada.png)