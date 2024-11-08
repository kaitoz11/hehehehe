using System.Linq.Expressions;
using Microsoft.EntityFrameworkCore;

namespace DataAccess;

public class DAO<T> : IDAO<T> where T : class
{
    private readonly ViroCureFal2024dbContext _context;
    public DAO()
    {
        _context ??= new ViroCureFal2024dbContext();
    }
    public void Add(T entity)
        => _context.Set<T>().Add(entity);

    public void Delete(T entity)
        => _context.Set<T>().Remove(entity);

    public async Task<T?> GetAsync(Expression<Func<T, bool>> expression = null!, CancellationToken cancellationToken = default)
        => await _context.Set<T>().FirstOrDefaultAsync(expression, cancellationToken);

    public async Task<List<T>> GetsAsync(Expression<Func<T, bool>> expression = null!, CancellationToken cancellationToken = default)
        => await _context.Set<T>().Where(expression).ToListAsync(cancellationToken);

    public async Task SaveChangesAsync(CancellationToken cancellationToken = default)
        => await _context.SaveChangesAsync(cancellationToken);
}