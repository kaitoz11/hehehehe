using System.Linq.Expressions;

namespace DataAccess;

public interface IDAO<T> where T : class
{
    void Add(T entity);
    void Delete(T entity);
    Task<T?> GetAsync(Expression<Func<T, bool>> expression = null!, CancellationToken cancellationToken = default);
    Task<List<T>> GetsAsync(Expression<Func<T, bool>> expression, CancellationToken cancellationToken = default);
    Task SaveChangesAsync(CancellationToken cancellationToken = default);
}