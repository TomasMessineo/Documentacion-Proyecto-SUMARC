
## Observaciones:

1. Si en las referencias se indica un número electrónico (por ejemplo e123) en vez de un rango de página (por ejemplo 10-15) no se realiza el enriquecimiento. Esto se debe a una falla en la regex de Journal (en JournalExpression.php) donde nunca se evalúa la existencia de un número electrónico.

2. Si el ultimo y el ante último autor de una referencia se separan mediante un "and" en vez de "y", no se lleva a cabo el enriquecimiento.