using System.Linq.Expressions;
using DataAccess;

namespace Repositories;

public class Repository<T> : IRepository<T> where T : class
{
    private readonly IDAO<T> _repository;
    public Repository()
    {
        _repository ??= new DAO<T>();
    }
    public void Add(T entity)
        => _repository.Add(entity);

    public void Delete(T entity)
        => _repository.Delete(entity);

    public async Task<T?> GetAsync(Expression<Func<T, bool>> expression = null!, CancellationToken cancellationToken = default)
        => await _repository.GetAsync(expression, cancellationToken);

    public async Task<List<T>> GetsAsync(Expression<Func<T, bool>> expression = null!, CancellationToken cancellationToken = default)
        => await _repository.GetsAsync(expression, cancellationToken);

    public async Task SaveChangesAsync(CancellationToken cancellationToken = default)
        => await _repository.SaveChangesAsync(cancellationToken);
}